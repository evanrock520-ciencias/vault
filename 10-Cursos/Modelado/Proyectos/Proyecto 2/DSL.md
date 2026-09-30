La gramática del lenguaje de dominio está inspirada en el lenguaje de búsquedas de **Github**.

Los filtros por categoría, son
```txt
artist: "Geordie Greep"
band: "Black Midi"
album: "Odyssey and Oracle"
song: "Opus"
```

Los filtros temporales
```txt
from: 1990
from: 1990 to 2000
```

Las operaciones lógicas básicas;
```
artist: "Angel Olsen" and album: "All Mirrors"

// Or inferido por contexto
artist: "Angel Olsen" or "Sharon Van Eten" 

// Or separado
artist: "Phoebe Bridgers" or band: "The National"
```

Orden:

```txt
sort: order by kind

// Donde
kind = artist | album | song | band | release

// Donde
order = asc | desc
```