# MuQL (Musical Query Language)
## 1. Léxico

```ebnf
(* Tokens *)
WORD      = ? secuencia de caracteres sin espacios, comillas, paréntesis ni ":" ? ;
STRING    = '"' { carácter | '\"' | '\\' } '"' ;
INTEGER   = dígito { dígito } ;
SYMBOLS   = ":" | "=>" | "(" | ")" ;

(* Palabras reservadas (sin distinguir mayúsculas) *)
RESERVED  = "and" | "or" | "not" | "like" | "by" | "asc" | "desc"
          | "sort" | "similar" | "from" | "to" | "year" | "track"
          | "performer" | "artist" | "band" | "album" | "song"
          | "genre" | "member" | "path" ;
```

- Los espacios y saltos de línea separan tokens y por lo demás se ignoran.
- Una palabra reservada usada como valor **debe ir entre comillas**: `band: "The Not"`.
- => es un token de dos caracteres: `1990=>2025` y `1990 => 2025` son equivalentes.

## 2. Sintaxis (EBNF)

```ebnf
query       = [ expr ] { sort } ;

(* Lógica, de menor a mayor precedencia: or < and < not *)
expr        = or_expr ;
or_expr     = and_expr { "or" and_expr } ;
and_expr    = not_expr { [ "and" ] not_expr } ;      (* "and" implícito *)
not_expr    = "not" not_expr | primary ;
primary     = "(" expr ")" | filter | term ;

term        = value ;                                (* búsqueda libre *)

filter      = text_filter | year_filter | bound_filter
            | track_filter | similar_filter ;

(* Filtros de texto *)
text_filter = text_field ":" value_list ;
text_field  = "performer" | "artist" | "band" | "album" | "song"
            | "genre" | "member" | "path" ;
value_list  = value { "or" value } ;                 (* "or" implícito *)

(* Filtros numéricos y temporales *)
year_filter  = "year" ":" range_list ;
bound_filter = ( "from" | "to" ) ":" INTEGER ;       (* azúcar de year *)
track_filter = "track" ":" range_list ;

range_list  = range_item { "or" range_item } ;
range_item  = INTEGER [ "=>" [ INTEGER ] ]
            | "=>" INTEGER ;

(* Apariencia *)
similar_filter = "similar" ":" sim_field "like" value ;
sim_field      = "song" | "performer" | "album" | "genre" ;

(* Orden *)
sort        = "sort" ":" [ order ] "by" sort_key ;
order       = "asc" | "desc" ;                       (* por omisión: asc *)
sort_key    = "song" | "performer" | "artist" | "band"
            | "album" | "release" | "track" ;

value       = STRING | WORD ;
```

## 3. Reglas de desambiguación

Estas reglas no se pueden expresar en la EBNF, pero el parser las necesita.

1. **`or` implícito (lista de valores).** Tras un `or`, mira el token siguiente:
    - Si es `campo:`, `not` o `(`, el `or` es **lógico** (nivel `or_expr`).
    - Si es un valor (o un entero/=> dentro de `year` y `track`), **continúa la lista** del filtro anterior.
2. **`and` implícito.** Si, terminado un `primary`, el token siguiente puede iniciar otro `primary` (valor, `campo:`, `not`, `(`), se inserta un `and`. Si el siguiente es `sort`, `or`, `)` o fin de entrada, no.
3. **`and` no hereda campo.** `performer: "A" and "B"` equivale a `performer: "A" and <búsqueda libre "B">`.
4. **`X not Y` ≡ `X and not Y`.**
5. **`sort`** solo va al final de la consulta, nunca dentro de paréntesis.
6. **Consulta vacía o solo con `sort`** es válida y devuelve toda la biblioteca.

## 4. Reglas semánticas

**Coincidencia**

| Elemento                                                          | Regla                                                                                                              |
| ----------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| `performer`, `artist`, `band`, `album`, `song`, `genre`, `member` | _contains_, sin distinguir mayúsculas ni acentos                                                                   |
| `path`                                                            | prefijo sobre la ruta, con separador `/` (`Music/Prog` incluye `Music/Prog/Yes`)                                   |
| Búsqueda libre                                                    | _contains_ en título, álbum, performer y género                                                                    |
| `similar`                                                         | _contains_ con tolerancia a erratas: distancia de edición ≤ 1 en palabras de hasta 5 letras, ≤ 2 en las más largas |

**Categorías**

- `performer` = unión de `artist` y `band`. Ambos los define el usuario.
- `member` lo define el usuario y devuelve las canciones de bandas que lo incluyen entre sus miembros.

**Rangos (`year`, `track`)**

- Ambos extremos son inclusivos.
- `5` ≡ `5 => 5`. `2010 =>` es abierto por la derecha y => 2000 por la izquierda.
- `a => b` con `a > b` es error.
- Un => sin ningún número es error.
- `year` filtra por el **año de lanzamiento de la canción**.
- `track: 3` es válido sin `album` y aplica a cualquier álbum.

**`from` / `to`**

```txt
from: X   ≡   year: X =>
to: Y     ≡   year: => Y
```

Varios filtros `year` unidos por `and` se intersectan: `year: 2000 => 2020 from: 2010` da 2010 => 2020.

**`not`**

- Es prefijo y unario, y aplica a un filtro, a un término o a un grupo.
- `not year: 1990 => 1999` excluye esa década.

**Orden**

- Los `sort` se aplican en orden de aparición (el primero es el criterio principal).
- `release` es el año de la canción. `artist` y `band` ordenan por el nombre del performer correspondiente.
- Desempate final: título de la canción (asc).
- Sin `sort`: primero las coincidencias exactas y luego las aproximadas si hay `similar`. En cualquier otro caso, título asc.

## 5. Precedencia

```txt
not  >  and (explícito o implícito)  >  or (lógico)
```

El `or` implícito entre valores de un filtro no entra en la tabla, porque es una lista de valores y se resuelve dentro del filtro.

## 6. Errores de validación

- Un año o pista no numérico: `se esperaba un número después de "year:"`.
- Rango invertido (`2020 => 2010`).
- => sin números.
- Paréntesis sin cerrar.
- `sort` dentro de paréntesis.
- Palabra reservada usada como valor sin comillas.
- Cadena sin cerrar.

## 7. Ejemplos

**Filtros por categoría**

```txt
performer: "Angel Olsen"
artist: "Geordie Greep"
band: "Black Midi"
album: "Odyssey and Oracle"
song: "Opus"
genre: "Art Pop"
member: "Steven Wilson"
path: "Music/Prog"
track: 3
track: 1 => 5
```

**Temporales**

```txt
from: 1990
to: 2025
year: 1990 => 2025
year: 2010 =>
year: => 2000
year: 2020
year: 1990 => 1999 or 2010 => 2015
```

**Apariencia**

```txt
similar: song like "Black"
similar: performer like "Phoebe"
```

**Lógica**

```txt
performer: "Angel Olsen" and album: "All Mirrors"
performer: "Angel Olsen" not album: "Big Time"
performer: "Angel Olsen" or "Sharon Van Etten"
performer: "Phoebe Bridgers" or performer: "The National"
(performer: "Angel Olsen" or "Sharon Van Etten") and not album: "Big Time"
member: "Steven Wilson" and not band: "Porcupine Tree"
not year: 1990 => 1999
```

**Orden**

```txt
sort: asc by song
sort: desc by release
sort: by album
album: "All Mirrors" sort: asc by album sort: asc by track
```

**Búsqueda libre y combinados**

```txt
"Love"
genre: "Art Pop" from: 2010 to: 2020 sort: desc by release
genre: "Art Pop" year: 2000 => 2010 track: 1 => 3
similar: song like "Black" from: 1990 sort: asc by release
performer: "Angel Olsen" or "Sharon Van Etten" not album: "Big Time"
// ≡ performer: ("Angel Olsen" or "Sharon Van Etten") and not album: "Big Time"
```

