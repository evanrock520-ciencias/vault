La gramática del lenguaje de dominio está inspirada en el lenguaje de búsquedas de GitHub.  
Los filtros por categoría son:

```txt
performer: "Angel Olsen"
// performer abarca tanto a artist como a band
artist: "Geordie Greep"
band: "Black Midi"

album: "Odyssey and Oracle"
song: "Opus"
genre: "Art Pop"
track: 3
path: "Music/Prog"
member: "Steven Wilson"
```

Los filtros temporales:

```txt
from: 1990
from: 1990 to 2000
to: 2025
```

Las operaciones lógicas básicas:

```txt
performer: "Angel Olsen" and album: "All Mirrors"

performer: "Angel Olsen" not album: "Big Time"

// Or inferido por contexto
performer: "Angel Olsen" or "Sharon Van Etten"

// Or separado
performer: "Phoebe Bridgers" or performer: "The National"
```

Orden:

```txt
sort: order by kind
sort: asc by song

// Donde
kind = artist | album | song | band | release

// Donde
order = asc | desc
```

Por omisión, una búsqueda del estilo:

```txt
"Love"
```

busca en todos los campos (título, álbum, intérprete y género).

La precedencia es:

```txt
not > and > or
```

Los términos seguidos sin operador se unen con `and` implícito, de modo que `X not Y` equivale a `X and not Y`. Se pueden usar paréntesis para agrupar.

```txt
performer: "Angel Olsen" or "Sharon Van Etten" not album: "Big Time"
// equivale a: (Angel Olsen or Sharon Van Etten) and not album "Big Time"

genre: "Art Pop" from: 2010 to 2020 sort: desc by release
```

---

## Gramática EBNF

```txt
(* Consulta completa *)
query        = [ expr ] , [ sort_clause ] ;

(* Expresiones booleanas, de menor a mayor precedencia *)
expr         = or_expr ;
or_expr      = and_expr , { "or" , and_expr } ;
and_expr     = unary_expr , { [ "and" ] , unary_expr } ;  (* "and" opcional = and implícito *)
unary_expr   = "not" , unary_expr
             | primary ;
primary      = "(" , expr , ")"
             | filter
             | free_text ;

(* Filtros *)
filter       = text_filter | track_filter | time_filter ;

text_filter  = text_field , ":" , string , { "or" , string } ;  (* or contextual *)
text_field   = "performer" | "artist" | "band" | "album"
             | "song" | "genre" | "path" | "member" ;

track_filter = "track" , ":" , integer ;

time_filter  = "from" , ":" , year , [ "to" , year ]
             | "to" , ":" , year ;

(* Texto libre *)
free_text    = string ;

(* Ordenamiento *)
sort_clause  = "sort" , ":" , order , "by" , kind ;
order        = "asc" | "desc" ;
kind         = "artist" | "band" | "album" | "song" | "release" ;

(* Léxico *)
string       = '"' , { character - '"' } , '"' ;
integer      = digit , { digit } ;
year         = digit , digit , digit , digit ;
```