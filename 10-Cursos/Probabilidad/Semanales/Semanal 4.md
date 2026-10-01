---
tipo: evaluacion
categoria: semanal
curso: "[[Probabilidad]]"
fecha: 2026-10-01
estado: pendiente
peso:
calificacion:
temas: []
---

# Semanal 4

## Temas que entran
- Variables Aleatorias Discretas
	- Bernoulli
	- Binomial
	- Poisson
	- Geométrica

## Resultado
**Calificación:** 

## Ejercicios
---
### Ejercicio 1: construir la masa y la distribución

Una caja tiene 5 fichas rojas, 3 azules y 2 amarillas. Se sacan 2 fichas al azar **sin reemplazo**. Ganas $3 por cada ficha azul, pierdes $2 por cada roja y las amarillas no cuentan. Sea $X$ la ganancia total.

Definimos:
- $N_{R}$ = número de bolas rojas seleccionadas
- $N_{A} =$ número de bolas azules seleccionadas.

Con lo que:
$$X = 3 \cdot N_{A} - 2 \cdot N_{R}$$
Así, si tomamos $2$ bolas.
- (R, R) $\Rightarrow$ $X = -2 \cdot 2 = -4$ 
- (R, Y) $\Rightarrow$ $X = -2$
- (R, A) $\Rightarrow$ $X = 3 - 2 = 1$ 
- (R, A) $\Rightarrow$ $X = 3 - 2 = 1$
- (R, Y) $\Rightarrow$ $X = 3$
- (A, A) $\Rightarrow$ $X = 3 \cdot 2 = 6$ 

Es decir:
$$X \in \{-4, -2, 1, 3, 6\}$$
De está manera:
$$P(X = -4) = \frac{\binom{5}{2}}{\binom{10}{2}}$$
$$P(X = -2) = \frac{\binom{5}{1} \cdot \binom{2}{1}}{\binom{10}{2}}$$
$$P(X = 1) = \frac{\binom{5}{1} \cdot \binom{3}{1}}{\binom{10}{2}}$$
$$P(X = 1) = \frac{\binom{5}{1} \cdot \binom{2}{1}}{\binom{10}{2}}$$
$$P(X = 3) = \frac{\binom{3}{1} \cdot \binom{2}{1}}{\binom{10}{2}}$$
$$P(X = 6) = \frac{\binom{3}{2}}{\binom{10}{2}}$$


## Qué falló
- **Error:** 
- **Corrección:** 
- **Tipo:** conceptual / algebraico / de lectura