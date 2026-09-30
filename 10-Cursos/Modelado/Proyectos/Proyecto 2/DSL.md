La gramática del lenguaje de dominio está inspirada en el lenguaje de búsquedas de **Github**.

Los filtros por categoría, son
```txt
performer: "Angel Olsen" 
// Perfomer puede derivarse a artist y band
artist: "Geordie Greep"
band: "Black Midi"

album: "Odyssey and Oracle"
song: "Opus"
genre: "Art Pop" 
track: 3 
path: "Music/Prog" 
member: "Steven Wilson"
```

Los filtros temporales
```txt
from: 1990
from: 1990 to 2000
to: 2025
```

Las operaciones lógicas básicas;
```
perfomer: "Angel Olsen" and album: "All Mirrors"

performer: "Angel Olsen" not album: "Big Time"

// Or inferido por contexto
performer: "Angel Olsen" or "Sharon Van Eten" 

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

Por omisión, una búsqueda del estilo
```txt
"Love"
```
Busca en todos los campos.

La precedencia se da:

```txt
not  >  and  >  or
```
