---
tipo: curso
semestre: 2026-2
---

# Matemáticas Aplicadas III

## Temario
- **1.** Integración de funciones de varias variables.
- **2.** Funciones con valores vectoriales.
- **3.** Integral sobre trayectorias y superficies.
- **4.** Teoremas de Green, Stokes y Gauss.

## Evaluación
-

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