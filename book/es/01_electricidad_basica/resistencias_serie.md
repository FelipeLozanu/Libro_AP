# Resistencias en serie

En una conexión en serie, la corriente pasa por una resistencia y después por la siguiente, sin caminos alternativos.

*Esquema simple de tres resistencias conectadas en serie.*

```{kroki}
:type: ditaa
:align: center

+--------+---+--------+---+--------+---+--------+
| Pila   |   |   R1   |   |   R2   |   |   R3   |
|        |   |        |   |        |   |        |
|        |   |        |   |        |   |        |
+--------+---+--------+---+--------+---+--------+
```

## Regla básica

$$
R_{eq} = R_1 + R_2 + R_3 + \dots
$$

## Ejercicio 1

Tres resistencias de $2\ \Omega$, $3\ \Omega$ y $5\ \Omega$ están conectadas en serie.

*Imagen del ejercicio 1: circuito en serie con resistencias de 2 ohm, 3 ohm y 5 ohm.*

```{kroki}
:type: ditaa
:align: center

+-----------+---+----------+---+----------+---+----------+
| Pila 10 V |   | R1: 2 ohm|   | R2: 3 ohm|   | R3: 5 ohm|
+-----------+---+----------+---+----------+---+----------+
```

1. Calcula la resistencia equivalente.
2. Si la pila es de $10\ V$, calcula la intensidad total.

```{admonition} Solución
:class: dropdown

Primero sumamos las resistencias:

$$
R_{eq} = 2 + 3 + 5 = 10\ \Omega
$$

Ahora aplicamos la ley de Ohm:

$$
I = \frac{V}{R} = \frac{10}{10} = 1\ A
$$

Respuesta: la resistencia equivalente es $10\ \Omega$ y la intensidad total es $1\ A$.
```

## Ejercicio 2

En un circuito en serie hay dos resistencias iguales de $6\ \Omega$ y una batería de $12\ V$.

*Imagen del ejercicio 2: dos resistencias iguales de 6 ohm conectadas en serie a una batería de 12 V.*

```{kroki}
:type: ditaa
:align: center

+-----------+---+----------+---+----------+
| Pila 12 V |   | R1: 6 ohm|   | R2: 6 ohm|
+-----------+---+----------+---+----------+
```

1. Halla la resistencia equivalente.
2. Calcula la intensidad del circuito.
3. Calcula la caída de tensión en cada resistencia.

```{admonition} Solución
:class: dropdown

La resistencia equivalente es:

$$
R_{eq} = 6 + 6 = 12\ \Omega
$$

La intensidad total es:

$$
I = \frac{12}{12} = 1\ A
$$

La caída de tensión en cada resistencia vale:

$$
V = I \cdot R = 1 \cdot 6 = 6\ V
$$

Respuesta: $R_{eq}=12\ \Omega$, $I=1\ A$ y en cada resistencia caen $6\ V$.
```

## Ejercicio 3

Diseña un circuito en serie con tres resistencias cuya resistencia equivalente sea $15\ \Omega$. Escribe una posible combinación y explica por qué funciona.

*Imagen del ejercicio 3: una posible combinación en serie de 4 ohm, 5 ohm y 6 ohm.*

```{kroki}
:type: ditaa
:align: center

+--------+---+----------+---+----------+---+----------+
| Pila   |   | R1: 4 ohm|   | R2: 5 ohm|   | R3: 6 ohm|
+--------+---+----------+---+----------+---+----------+
```

```{admonition} Posible respuesta
:class: dropdown

Una opción es usar $4\ \Omega$, $5\ \Omega$ y $6\ \Omega$.

$$
4 + 5 + 6 = 15\ \Omega
$$

Funciona porque en serie la resistencia equivalente siempre es la suma directa.
```
