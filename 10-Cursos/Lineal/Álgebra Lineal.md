---
tipo: curso
semestre: 2026-2
---

# Álgebra Lineal

## Temario
- Espacios vectoriales.
- Matrices.
    2.1 Sistemas de ecuaciones lineales.
- Transformaciones lineales.
- Transformaciones lineales y matrices
- Determinantes.
- Producto escalar*.
- Transformaciones simétricas*

## Evaluación
- 100% Parciales

## Evaluaciones
```dataview
TABLE categoria, fecha, peso, estado, calificacion
FROM "10-Cursos"
WHERE tipo = "evaluacion" AND curso = this.file.link
SORT fecha ASC
```

## Conceptos
```dataview
TABLE categoria, dominio
FROM "10-Cursos"
WHERE tipo = "concepto" AND curso = this.file.link
SORT dominio ASC
```

## Clases
```dataview
LIST
FROM "10-Cursos"
WHERE tipo = "clase" AND curso = this.file.link
SORT fecha DESC
```

## Enlaces
- [[Cuaderno de errores]]