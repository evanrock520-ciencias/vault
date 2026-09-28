## Próximas evaluaciones
```dataview
TABLE curso, categoria, fecha, peso, estado
FROM "10-Cursos"
WHERE tipo = "evaluacion" AND estado != "calificado" AND fecha >= date(today)
SORT fecha ASC
```

## Proyectos activos
```dataview
TABLE curso, entrega, estado, repo
FROM "10-Cursos"
WHERE tipo = "proyecto" AND estado != "entregado"
SORT entrega ASC
```

## Tareas de los próximos 7 días
```tasks
not done
due before in 7 days
group by filename
sort by due
```

## Conceptos por reforzar
```dataview
TABLE curso, dominio
FROM "10-Cursos"
WHERE tipo = "concepto" AND dominio != "demostrado"
SORT curso ASC
```

## Calificaciones
```dataview
TABLE WITHOUT ID curso, categoria, calificacion, peso
FROM "10-Cursos"
WHERE tipo = "evaluacion" AND calificacion
SORT curso ASC
```