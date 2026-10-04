---
tipo: proyecto
curso: "[[Modelado y Programación]]"
estado: pendiente
entrega:
repo: https://github.com/evanrock520-ciencias/8-Track
equipo: []
---

# 8-Track

**Repo:** https://github.com/evanrock520-ciencias/8-Track
**Tablero:** [[Kanban Proyecto 2]]

## Requisitos
- Base de Datos
- Interfaz Gráfica (GTK, QT, JavaFX)
- Lenguaje de Dominio (para consultas)
- Minero de etiquetas ID3v2.4. Debe funcionar sin la interfaz también.

## Opcionales
- Reproductor MP3

## Diseño
### Decisiones
| Fecha      | Decisión                                           | Alternativas                             | Por qué                                                 |
| ---------- | -------------------------------------------------- | ---------------------------------------- | ------------------------------------------------------- |
| 28/09/2026 | Utilizar C++ y QT para desarrollar el proyecto.    | Rust e Iced, Go y Fyne                   | Me interesa aprender QT y estoy bastante cómodo con C++ |
| 2/10/2026  | Utilizar un DSL similar a las búsquedas de Github. | Tags con búsqueda avanzada.              | Es bastante legible y sencilla.                         |
| 3/10/2026  | Utilizar TagLib para implementar el minero         | Realizar el tagger completamente a mano. | Me ahorra bastante tiempo.                              |
| 3/10/2026  | Utilizar SQLite para la base de datos.             |                                          | Especificación del proyecto.                            |
| 4/10/2026  | Utilizar una estética neobrutalista                | Estilo pixel art                         | Me parece bonita.                                       |

## Bugs conocidos
- [ ] 

