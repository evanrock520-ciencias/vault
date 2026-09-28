---
tipo: curso
semestre: 2026-2
---

# Modelado y Programación

## Temario
- Comenzando un proyecto de la nada
    1. Análisis y diseño
    2. Implementación
    3. Distribución e instalación
    4. Mantenimiento
    5. Resumen
- Buenas prácticas de programación
    1. Código limpio
    2. Guías de estilo
    3. Refactorización
    4. Revisión de código
    5. Pruebas unitarias
    6. Desarrollo guiado por pruebas
    7. Patrones de diseño
- Paradigmas de programación
    1. Programación imperativa
    2. Programación declarativa
- Programación concurrente
    1. Procesos
    2. Hilos de ejecución
    3. Programación paralela
- Interfaces humano-computadora
    1. Interacción humano-computadora
    2. Interfaces gráficas
    3. Patrón MVC
- Bases de datos
    1. Introducción
    2. Sistema de administración de base de datos
    3. Bases de datos relacionales
    4. Álgebra relacional
    5. Bases de datos NoSQL
- Aplicaciones web
    1. Introducción
    2. Marcos de trabajo
    3. _Front-end_ y _back-end_
    4. Integración

## Evaluación
- 100% Proyectos

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