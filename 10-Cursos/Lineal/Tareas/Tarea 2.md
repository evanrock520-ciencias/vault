---
tipo: evaluacion
categoria: parcial
curso: "[[Álgebra Lineal]]"
fecha: 2026-10-09
estado: preparando
peso:
calificacion:
temas: []
---

# Tarea 2

## Temas
- [ ] Combinaciones Lineales
- [ ] Bases
- [ ] Dimensión
- [ ] Transformaciones Lineales

## Demostraciones clave
---
## Independencia lineal

- [x] **2.** Demostrar que el conjunto ${e_1, e_2, \dots, e_n}$ es linealmente independiente en $\mathbb{K}^n$. ✅ 2026-10-06
    
- [x] **3.** Demostrar que el conjunto ${1, x, \dots, x^n}$ es linealmente independiente en $P_n(\mathbb{K})$. ✅ 2026-10-06
    
- [x] **4.** Sean $u$ y $v$ dos vectores distintos en un espacio vectorial $V$. Demostrar que ${u, v}$ es linealmente dependiente si, y solamente si $u$ es múltiplo de $v$ o $v$ es múltiplo de $u$. ✅ 2026-10-06

**P.D**: $\{u,v\}$ es linealmente dependiente $\iff u = kv$ ó $v = ku$ para alguna $k \in K$.
($\implies$) Por hipótesis $0 = k_{1}v +  k_{2}u$ donde o bien $k_{1} \neq 0$ ó $k_{2} \neq 0$. 
Si $k_{1} \neq 0$, como $K$ es campo $\implies \exists k_{1}^{-1} \in K$. Así:
$$k_{1}v + k_{2}u = 0 \implies k_{1}v = -k_{2}u \implies v = (k_{1}^{-1}k_{2}u) \implies v = ku$$

Si $k_{2} \neq 0$, como $K$ es campo $\implies \exists k_{2}^{-1} \in K$. Así:
$$k_{1}v + k_{2}u = 0 \implies k_{2}u = -k_{1}v \implies u = (k_{2}^{-1}k_{1}v) \implies u = kv$$
$\therefore u = kv$ ó $v = ku$ para alguna $k \in K$$

($\impliedby$) Tenemos 2 casos.
1. Si $u = kv \implies 1 \cdot u - kv = 0$, y como $1 \neq 0 \implies$ no es la combinación trivial. 
$\therefore \{u,v\}$ es linealmente dependiente.
El otro caso es análogo.

$\therefore$ $\{u,v\}$ es linealmente dependiente $\iff u = kv$ ó $v = ku$ para alguna $k \in K$

- [ ] **5.** Sea $V$ un $\mathbb{K}$-espacio vectorial (con $\mathbb{K}$ un campo cuya característica no es dos) y sean ${u, v} \subset V$. Demostrar que ${u, v}$ es linealmente independiente si y solamente si ${u+v,, u-v}$ es linealmente independiente.
    
- [ ] **6.** Demostrar que un conjunto $S$ es linealmente dependiente si, y solamente si $S = {0}$ o existen $v, u_1, u_2, \dots, u_n$ vectores distintos en $S$ tales que $v$ es una combinación lineal de $u_1, u_2, \dots, u_n$.

**P.D:** $S$ es linealmente dependiente si, y solamente si $S = {0}$ o existen $v, u_1, u_2, \dots, u_n$ vectores distintos en $S$ tales que $v$ es una combinación lineal de $u_1, u_2, \dots, u_n$.

**($\implies$)** Sean $v_1, \dots, v_n$ y $c_1, \dots, c_n$. Elige $j$ con $c_j \neq 0$. Hay dos casos según $n$.

**Caso 1: $n = 1$.** Entonces $c_1 w_1 = 0$ con $c_1 \neq 0$, así que $w_1 = c_1^{-1}\cdot 0 = 0$. Ahora hay dos opciones:

- Si $S = {0}$, ya terminaste.
- Si $S \neq {0}$, existe $u \in S$ con $u \neq 0$. Entonces $0$ y $u$ son vectores distintos de $S$ y  
    $$0 = 0\cdot u,$$  
    o sea que $v = 0$ es combinación lineal de $u_1 = u$ (con $k_1 = 0$).

**Caso 2: $m \geq 2$.** Como $c_j \neq 0$, existe $c_j^{-1} \in \mathbb{K}$. Despejando $w_j$ en  
$$c_jw_j = -\sum_{i \neq j} c_iw_i,$$  
queda  
$$w_j = \sum_{i \neq j} \left(-c_j^{-1}c_i\right) w_i.$$  
Toma $v = w_j$ y como $u_1, \dots, u_{m-1}$ los $w_i$ con $i \neq j$. Son vectores distintos de $S$ (porque los $w_i$ lo eran), hay al menos uno ($m - 1 \geq 1$), y $v$ es combinación lineal de ellos. $\blacksquare$

**($\impliedby$)**

1. Si $S = {0}$, entonces $1\cdot 0 = 0$ con coeficiente $1 \neq 0$. Luego $S$ es linealmente dependiente.
    
2. Si existen $v, u_1, \dots, u_n \in S$ distintos con $v = k_1u_1 + \dots + k_nu_n$, entonces  
    $$0 = 1\cdot v - k_1u_1 - \dots - k_nu_n.$$  
    Como los vectores son distintos, el coeficiente de $v$ es $1 \neq 0$, así que la combinación es no trivial. Luego $S$ es linealmente dependiente. $\blacksquare$
	
- [ ] **7.** Sea $S := {u_1, u_2, \dots, u_n}$ un conjunto finito de vectores. Demostrar que $S$ es linealmente dependiente si, y solamente si $u_1 = 0$ o $u_{k+1} \in \text{span}({u_1, u_2, \dots, u_k})$ para alguna $1 \le k < n$.
    
- [ ] **8.** Sea $V$ un $\mathbb{K}$-espacio vectorial.
    
    - Si $T_1 \subseteq T_2 \subseteq V$ y $T_1$ es linealmente dependiente, demostrar que $T_2$ es linealmente dependiente.
    - Si $T_1 \subseteq T_2 \subseteq V$ y $T_2$ es linealmente independiente, demostrar que $T_1$ es linealmente independiente.

---

## Bases y dimensión

- [ ] **9.** Decidir si cada afirmación es verdadera o falsa. _(Justificar adecuadamente sus respuestas)_
    
    - (a) El espacio vectorial cero no tiene base.
    - (b) Todo espacio vectorial que es generado por un conjunto finito tiene una base.
    - (c) Todo espacio vectorial tiene una base finita.
    - (d) Un espacio vectorial no puede tener más de una base.
    - (e) Si un espacio vectorial tiene una base finita, entonces el número de vectores en toda base es el mismo.
    - (f) La dimensión de $P_n(\mathbb{K})$ es $n$.
    - (g) La dimensión de $M_{m\times n}(\mathbb{K})$ es $m+n$.
    - (h) Sea $V$ un espacio vectorial de dimensión finita, $S_1$ un subconjunto linealmente independiente de $V$ y $S_2$ un subconjunto de $V$ que genera a $V$. Entonces $S_1$ no puede tener más vectores que $S_2$.
    - (i) Si $S$ genera el espacio vectorial $V$, entonces todo vector en $V$ puede escribirse como combinación lineal de los vectores en $S$ de una única manera.
    - (j) Todo subespacio de un $V$ espacio vectorial de dimensión finita es de dimensión finita.
    - (k) Si $V$ es un espacio vectorial de dimensión $n$, entonces $V$ tiene exactamente un subespacio de dimensión $0$ y exactamente un subespacio de dimensión $n$.
    - (l) Si $V$ es un espacio vectorial de dimensión $n$, y si $S$ es un subconjunto de $V$ con $n$ vectores, entonces $S$ es linealmente independiente si, y solo si, $S$ genera $V$.
- [ ] **16.** Sea $\mathbb{K}$ un campo infinito y considerar a $V = \mathbb{K}$ como $\mathbb{K}$-espacio vectorial.
    
    - Encontrar una base para este espacio vectorial.
    - Calcular su dimensión.
    - Describir una infinidad de bases distintas para este espacio vectorial.
- [ ] **17.** Sea $V$ un $\mathbb{K}$-espacio vectorial de dimensión finita. Demostrar que $\beta := {v_1, \dots, v_n}$ es base de $V$ si y sólo si $\alpha\cdot\beta := {\alpha\cdot v_1, \dots, \alpha\cdot v_n}$ es base de $V$ con $\alpha \in \mathbb{K}\setminus{0}$.
    
- [ ] **22.** Sea $V$ un $\mathbb{K}$-espacio vectorial y ${u, v} \subset V$ vectores distintos. Mostrar que si ${u, v}$ es una base de $V$ y ${a, b} \subset \mathbb{K}\setminus{0}$, entonces tanto ${u+v,, a\cdot u}$ como ${a\cdot u,, b\cdot v}$ también son bases de $V$.
    
- [ ] **24.** Sea $V$ un $\mathbb{K}$-espacio vectorial tal que existe $\beta \subset V$ base de $V$ con $|\beta| = n$ ($n \in \mathbb{N}$). Demostrar que cualquier otra base de $V$ tiene $n$ elementos.
    
- [ ] **25.** Sea $V$ un $\mathbb{K}$-espacio vectorial de dimensión $n$. Demostrar que:
    
    - Cualquier conjunto generador finito de $V$ contiene al menos $n$ vectores. Más aún, un conjunto generador de $V$ que contiene exactamente $n$ vectores es una base de $V$.
    - Cualquier subconjunto linealmente independiente de $V$ contiene a lo más $n$ vectores. Más aún, un conjunto linealmente independiente de $V$ que contiene exactamente $n$ vectores es una base de $V$.
    - Cualquier subconjunto linealmente independiente de $V$ puede ser extendido a una base de $V$.
- [ ] **26.** El conjunto de soluciones del sistema de ecuaciones lineales
    
    $$ \begin{cases} 2x_1 - 2x_2 + 3x_3 = 0,\ 2x_1 + 3x_2 + 3x_3 = 0, \end{cases} $$
    
    es un subespacio de $\mathbb{R}^3$. Encontrar una base de este subespacio.
    
- [ ] **31.** Sea $V$ un $\mathbb{K}$-espacio vectorial de dimensión $n$, y sea $S \subseteq V$ generador de $V$.
    
    - (a) Demostrar que existe un subconjunto de $S$ que es una base de $V$. (Tenga cuidado de no asumir que $S$ sea finito. _Sugerencia: El Teorema de Reemplazo puede ser útil._)
    - (b) Demostrar que $S$ contiene al menos $n$ vectores.
- [ ] **32.** Demostrar que un espacio vectorial es de dimensión infinita si y solo si contiene un subconjunto linealmente independiente infinito. _(Sugerencia: El Teorema de Reemplazo y el ejercicio anterior (31) pueden ser de utilidad.)_
    

---

## Subespacios, suma e intersección

- [ ] **34.** Sean $W_1$ y $W_2$ subespacios de un $\mathbb{K}$-espacio vectorial de dimensión finita $V$. Determinar condiciones necesarias y suficientes sobre $W_1$ y $W_2$ tales que
    
    $$\dim(W_1 \cap W_2) = \dim(W_1).$$
    
- [ ] **39.** Sea $V$ un $\mathbb{K}$-espacio vectorial y sean $W_1$ y $W_2$ subespacios de dimensión finita.
    
    - (a) Demostrar que el subespacio $W_1 + W_2$ _(recordar que $W_1 + W_2 := {u + v \mid u \in W_1 ;&; v \in W_2}$)_ es de dimensión finita, y
        
        $$\dim(W_1 + W_2) = \dim(W_1) + \dim(W_2) - \dim(W_1 \cap W_2).$$
        
        _Sugerencia:_ Comenzar con una base ${u_1, u_2, \dots, u_k}$ de $W_1 \cap W_2$ y extender este conjunto a una base ${u_1, \dots, u_k, v_1, \dots, v_m}$ de $W_1$ y a una base ${u_1, \dots, u_k, w_1, \dots, w_p}$ de $W_2$.
        
    - (b) Suponer que $V = W_1 + W_2$. Demostrar que $V = W_1 \oplus W_2$ si y solamente si $\dim(W_1 + W_2) = \dim(W_1) + \dim(W_2)$.
        
- [ ] **41.** Sea $V$ un $\mathbb{K}$-espacio vectorial y sean $W_1$ y $W_2$ subespacios con dimensiones $m$ y $n$, respectivamente, donde $m \ge n$.
    
    - (a) Demostrar que $\dim(W_1 \cap W_2) \le n$.
    - (b) Demostrar que $\dim(W_1 + W_2) \le m + n$.

---

## Transformaciones lineales

- [ ] **42.** Marcar las siguientes proposiciones como verdaderas o falsas. En cada parte, $V$ y $W$ son espacios vectoriales de dimensión finita sobre el campo $\mathbb{K}$, y $T$ es una función de $V$ a $W$.
    
    - a) Si $T$ es lineal, entonces $T$ preserva sumas y productos escalares.
    - b) Si $T(x+y) = T(x) + T(y)$, entonces $T$ es lineal.
    - c) $T$ es uno a uno si y solo si el único vector $x$ tal que $T(x) = 0$ es $x = 0$.
    - d) Si $T$ es lineal, entonces $T(0_V) = 0_W$.
    - e) Si $T$ es lineal, entonces $\text{Ker}(T) + \text{Im}(T) = \dim(V)$.
    - f) Si $T$ es lineal, entonces $T$ lleva subconjuntos linealmente independientes de $V$ a subconjuntos linealmente independientes de $W$.
    - g) Si $T, U: V \to W$ son lineales y están definidos sobre una base de $V$, entonces $T = U$.
    - h) Dados ${x_1, x_2} \subset V$ y ${y_1, y_2} \subset W$, existe una transformación lineal $T: V \to W$ tal que $T(x_1) = y_1$ y $T(x_2) = y_2$.
- [ ] **44.** Sean $V$ y $W$ $\mathbb{K}$-espacios vectoriales y $T: V \to W$ una función. Demostrar que:
    
    - Si $T$ es lineal entonces $T(0_V) = 0_W$. ¿Es cierto el recíproco?
    - $T$ es lineal si y sólo si $T(c\cdot u + v) = c\cdot T(u) + T(v)$ para todo ${u, v} \subset V$ y todo $c \in \mathbb{K}$.
    - Si $T$ es lineal entonces $T(u - v) = T(u) - T(v)$ para todo ${u, v} \subset V$. ¿Es cierto el recíproco?
    - $T$ es lineal si y sólo si para ${v_1, \dots, v_k} \subseteq V$ y ${c_1, \dots, c_k} \subseteq \mathbb{K}$ se tiene que $T!\left(\sum_{i=1}^{k} c_i\cdot v_i\right) = \sum_{i=1}^{k} c_i\cdot T(v_i)$.
- [ ] **55.** Sean $V$ y $W$ $\mathbb{K}$-espacios vectoriales, $T: V \to W$ lineal, y ${w_1, w_2, \dots, w_k} \subseteq \text{Im}(T)$ linealmente independiente. Demostrar que si $S = {v_1, v_2, \dots, v_k}$ se elige de modo que $T(v_i) = w_i$ para $i = 1, 2, \dots, k$, entonces $S$ es linealmente independiente.
    
- [ ] **56.** Sean $V$ y $W$ $\mathbb{K}$-espacios vectoriales y $T: V \to W$ lineal.
    
    - a) Demostrar que $T$ es inyectiva si y solo si $T$ lleva subconjuntos linealmente independientes de $V$ en subconjuntos linealmente independientes de $W$.
    - b) Suponer que $T$ es inyectiva y que $S \subseteq V$. Demostrar que $S$ es linealmente independiente si y solo si $T(S)$ lo es.
    - c) Suponer que $B = {v_1, v_2, \dots, v_n}$ es una base de $V$ y que $T$ es biyectiva. Demostrar que $T(B) = {T(v_1), T(v_2), \dots, T(v_n)}$ es una base de $W$.
- [ ] **59.** Sean $V$ y $W$ $\mathbb{K}$-espacios vectoriales de dimensión finita y $T: V \to W$ lineal.
    
    - a) Demostrar que si $\dim(V) < \dim(W)$, entonces $T$ no puede ser sobreyectiva.
    - b) Demostrar que si $\dim(V) > \dim(W)$, entonces $T$ no puede ser inyectiva.
- [ ] **62.** Sean $V$ y $W$ $\mathbb{K}$-espacios vectoriales con subespacios $V_1 \subseteq V$ y $W_1 \subseteq W$. Si $T: V \to W$ es lineal, demostrar que $T(V_1)$ es un subespacio de $W$ y que ${x \in V : T(x) \in W_1}$ es un subespacio de $V$.
    
- [ ] **64.** Sea $T: \mathbb{R}^3 \to \mathbb{R}$ lineal. Demostrar que existen escalares $a, b, c$ tales que
    
    $$T(x, y, z) = ax + by + cz$$
    
    para todo $(x, y, z) \in \mathbb{R}^3$. ¿Cómo generalizar este resultado para $T: \mathbb{K}^n \to \mathbb{K}$? Enunciar y demostrar un resultado análogo.
    

---

## Resumen de prioritarios

|Tema|Ejercicios ♣|
|---|---|
|Independencia lineal|2, 3, 4, 5, 6, 7, 8|
|Bases y dimensión|9, 16, 17, 22, 24, 25, 26, 31, 32|
|Subespacios, suma e intersección|34, 39, 41|
|Transformaciones lineales|42, 44, 55, 56, 59, 62, 64|

**Total:** 26 ejercicios.

## Definiciones a saber de memoria
- 

## Ejercicios tipo
- [ ] 

## Repaso final
- [ ] Revisar [[Cuaderno de errores]]
- [ ] Marcar `dominio` de cada concepto