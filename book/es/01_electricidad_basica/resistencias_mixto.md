# Circuitos mixtos

Un circuito mixto combina tramos en serie y tramos en paralelo. La idea principal es simplificar paso a paso.

*Esquema simple de un circuito mixto con una resistencia en serie y dos ramas en paralelo.*

```{kroki}
:type: ditaa
:align: center

+--------+---+------------------+---+------------------+
| Pila   |   | Resistencia serie|   |     Retorno      |
+--------+---+------------------+---+------------------+
				|                            ^
				|                            |
				+---+----------+---+---------+
				|   | Rama 1   |   |
				|   +----------+   |
				|   +----------+   |
				+---+ Rama 2   +---+
					+----------+
```

## Estrategia

1. Identifica qué resistencias están claramente en paralelo o en serie.
2. Sustituye ese grupo por una resistencia equivalente.
3. Repite el proceso hasta obtener una sola resistencia.

## Ejercicio 1

Una resistencia de $4\ \Omega$ está en serie con un bloque en paralelo formado por $6\ \Omega$ y $3\ \Omega$.

*Imagen del ejercicio 1: una resistencia de 4 ohm en serie con un paralelo de 6 ohm y 3 ohm.*

```{kroki}
:type: ditaa
:align: center

+--------+---+----------+---+--------+
| Pila   |   | R1: 4 ohm|   |Retorno |
+--------+---+----------+---+--------+
				|                ^
				|                |
				+---+----------+-+
				|   | R2: 6 ohm| |
				|   +----------+ |
				|   +----------+ |
				+---+ R3: 3 ohm+-+
					+----------+
```

1. Calcula la resistencia equivalente del paralelo.
2. Calcula la resistencia total del circuito.

```{admonition} Solución
:class: dropdown

Primero resolvemos el paralelo:

$$
\frac{1}{R_p} = \frac{1}{6} + \frac{1}{3} = \frac{1}{2}
$$

Por tanto:

$$
R_p = 2\ \Omega
$$

Ahora sumamos la resistencia en serie:

$$
R_{eq} = 4 + 2 = 6\ \Omega
$$
```

## Ejercicio 2

En un circuito hay dos resistencias de $8\ \Omega$ en paralelo y, a continuación, una resistencia de $4\ \Omega$ en serie.

*Imagen del ejercicio 2: dos resistencias de 8 ohm en paralelo seguidas por una de 4 ohm en serie con una batería de 12 V.*

```{kroki}
:type: ditaa
:align: center

+-----------+      /---+----------+---\
| Pila 12 V |--+---+   | R1: 8 ohm|   +---+----------+---+--------+
+-----------+  |   |   +----------+   |   | R3: 4 ohm|   |Retorno |
               |   +---+----------+---+   +----------+---+--------+
               |       | R2: 8 ohm|
               |       +----------+
```

1. Halla la resistencia del bloque en paralelo.
2. Calcula la resistencia total.
3. Si la batería es de $12\ V$, calcula la intensidad total.

```{admonition} Solución
:class: dropdown

Dos resistencias iguales en paralelo equivalen a la mitad:

$$
R_p = 4\ \Omega
$$

La resistencia total es:

$$
R_{eq} = 4 + 4 = 8\ \Omega
$$

La intensidad total vale:

$$
I = \frac{12}{8} = 1.5\ A
$$
```

## Ejercicio 3

Observa este esquema verbal: una resistencia de $2\ \Omega$ en serie con dos resistencias en paralelo de $4\ \Omega$ y $4\ \Omega$, y después otra resistencia de $2\ \Omega$ en serie.

*Imagen del ejercicio 3: circuito mixto con 2 ohm en serie, un paralelo de 4 ohm y 4 ohm, y otros 2 ohm en serie.*

```{kroki}
:type: ditaa
:align: center

+--------+---+----------+      /---+----------+---\
| Pila   |   | R1: 2 ohm|--+---+   | R2: 4 ohm|   +---+----------+---+--------+
+--------+---+----------+  |   |   +----------+   |   | R4: 2 ohm|   |Retorno |
                           |   +---+----------+---+   +----------+---+--------+
                           |       | R3: 4 ohm|
                           |       +----------+
```

Calcula la resistencia equivalente total.

```{admonition} Solución
:class: dropdown

El paralelo de $4\ \Omega$ y $4\ \Omega$ equivale a:

$$
R_p = 2\ \Omega
$$

Luego todo queda en serie:

$$
R_{eq} = 2 + 2 + 2 = 6\ \Omega
$$
```
