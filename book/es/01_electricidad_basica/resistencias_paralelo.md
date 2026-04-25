# Resistencias en paralelo

En una conexión en paralelo, la corriente tiene varios caminos posibles. El voltaje es el mismo en todas las ramas.

*Esquema simple de dos resistencias en paralelo.*

```{kroki}
:type: ditaa
:align: center

              /---+--------+---\
+--------+---+   |   R1   |   +---+--------+
| Pila   |   |   +--------+   |   | Retorno|
+--------+---+                +---+--------+
              \---+--------+---/
                  |   R2   |
                  +--------+
```

## Regla básica

Para dos resistencias:

$$
\frac{1}{R_{eq}} = \frac{1}{R_1} + \frac{1}{R_2}
$$

## Ejercicio 1

Dos resistencias de $6\ \Omega$ y $3\ \Omega$ están en paralelo.

*Imagen del ejercicio 1: dos resistencias de 6 ohm y 3 ohm en paralelo.*

```{kroki}
:type: ditaa
:align: center

              /---+----------+---\
+--------+---+   | R1: 6 ohm|   +---+--------+
| Pila   |   |   +----------+   |   | Retorno|
+--------+---+                  +---+--------+
              \---+----------+---/
                  | R2: 3 ohm|
                  +----------+
```

1. Calcula la resistencia equivalente.
2. ¿Es mayor o menor que la resistencia más pequeña?

```{admonition} Solución
:class: dropdown

Aplicamos la fórmula:

$$
\frac{1}{R_{eq}} = \frac{1}{6} + \frac{1}{3} = \frac{1}{6} + \frac{2}{6} = \frac{3}{6} = \frac{1}{2}
$$

Por tanto:

$$
R_{eq} = 2\ \Omega
$$

La resistencia equivalente es menor que la resistencia más pequeña, que era $3\ \Omega$.
```

## Ejercicio 2

Tres resistencias iguales de $12\ \Omega$ están conectadas en paralelo.

*Imagen del ejercicio 2: tres resistencias iguales de 12 ohm en paralelo con un generador de 12 V.*

```{kroki}
:type: ditaa
:align: center

                  /---+-----------+---\
+---------------+-+   | R1: 12 ohm|   +--+--------+
| Generador 12 V| |   +-----------+   |  | Retorno|
+---------------+-+                   +--+--------+
                  \---+-----------+---/
                      | R2: 12 ohm|
                      +-----------+
                  /---+-----------+---\
                  |   | R3: 12 ohm|   |
                  \---+-----------+---/
```

1. Calcula la resistencia equivalente.
2. Si el generador es de $12\ V$, calcula la intensidad total.

```{admonition} Solución
:class: dropdown

Si las tres son iguales:

$$
\frac{1}{R_{eq}} = \frac{1}{12} + \frac{1}{12} + \frac{1}{12} = \frac{3}{12} = \frac{1}{4}
$$

Así que:

$$
R_{eq} = 4\ \Omega
$$

La intensidad total es:

$$
I = \frac{V}{R} = \frac{12}{4} = 3\ A
$$
```

## Ejercicio 3

Explica con tus palabras por qué al añadir ramas en paralelo la resistencia equivalente disminuye.

*Imagen del ejercicio 3: al añadir ramas aparecen más caminos para la corriente.*

```{kroki}
:type: ditaa
:align: center

                  /---+--------+---\
+--------+---+   |   | Rama A |   |   +--------+
| Pila   |   +---+   +--------+   +---+ Retorno|
+--------+---+   |                  |   +--------+
                  |   +--------+   |
                  +---+ Rama B +---+
                  |   +--------+   |
                  |   +--------+   |
                  +---+ Rama C +---+
                      +--------+
```

```{admonition} Idea clave
:class: dropdown

Al poner ramas en paralelo aparecen más caminos para que circule la corriente. Cuantos más caminos haya, menos se opone el circuito al paso de la corriente y por eso la resistencia equivalente baja.
```
