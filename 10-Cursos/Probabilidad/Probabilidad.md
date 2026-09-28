---
tipo: curso
semestre: 2026-2
---

# Probabilidad

## Temario
- Fundamentos de la probabilidad
- Combinatoria
- Axiomas de la probabilidad
- Probabilidad condicional
- Variables aleatorias discretas
- Variables aleatorias continuas
- Funciones de variables aleatorias
- Valor esperado
- Momentos
- Desigualdades
- Funciones generadoras
- Distribución conjunta
- Valor esperado de vectores aleatorios
- Independencia de variables aleatorias
- Convergencia en distribución, probabilidad, media y convergencia casi segura
- Ley de los grandes números y el teorema central del límite

## Evaluación
- 50% Parciales
- 50% Semanales

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