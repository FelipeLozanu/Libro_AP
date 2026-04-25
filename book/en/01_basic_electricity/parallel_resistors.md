# Parallel Resistors

In a parallel connection, current has several possible paths. Voltage is the same across every branch.

*Simple diagram of two resistors connected in parallel.*

```{kroki}
:type: ditaa
:align: center

                 /---+-----------+---\
+---------+---+ |   |    R1     |   +---+--------+
| Battery |   +-+   +-----------+   |   | Return |
+---------+---+ |                   +---+--------+
                 \---+-----------+---/
                     |    R2     |
                     +-----------+
```

## Basic rule

For two resistors:

$$
\frac{1}{R_{eq}} = \frac{1}{R_1} + \frac{1}{R_2}
$$

## Exercise 1

Two resistors of $6\ \Omega$ and $3\ \Omega$ are connected in parallel.

*Exercise 1 image: 6 ohm and 3 ohm resistors connected in parallel.*

```{kroki}
:type: ditaa
:align: center

                 /---+----------+---\
+---------+---+ |   | R1: 6 ohm|   +---+--------+
| Battery |   +-+   +----------+   |   | Return |
+---------+---+ |                  +---+--------+
                 \---+----------+---/
                     | R2: 3 ohm|
                     +----------+
```

1. Calculate the equivalent resistance.
2. Is it greater or smaller than the smallest resistor?

```{admonition} Solution
:class: dropdown

Apply the formula:

$$
\frac{1}{R_{eq}} = \frac{1}{6} + \frac{1}{3} = \frac{1}{6} + \frac{2}{6} = \frac{3}{6} = \frac{1}{2}
$$

So:

$$
R_{eq} = 2\ \Omega
$$

The equivalent resistance is smaller than the smallest resistor, which was $3\ \Omega$.
```

## Exercise 2

Three equal resistors of $12\ \Omega$ are connected in parallel.

*Exercise 2 image: three equal 12 ohm resistors in parallel with a 12 V source.*

```{kroki}
:type: ditaa
:align: center

                  /---+-----------+---\
+-------------+--+   | R1: 12 ohm|   +--+--------+
| Source 12 V |  |   +-----------+   |  | Return |
+-------------+--+                   +--+--------+
                  \---+-----------+---/
                      | R2: 12 ohm|
                      +-----------+
                  /---+-----------+---\
                  |   | R3: 12 ohm|   |
                  \---+-----------+---/
```

1. Calculate the equivalent resistance.
2. If the source is $12\ V$, calculate the total current.

```{admonition} Solution
:class: dropdown

Since all three resistors are equal:

$$
\frac{1}{R_{eq}} = \frac{1}{12} + \frac{1}{12} + \frac{1}{12} = \frac{3}{12} = \frac{1}{4}
$$

Therefore:

$$
R_{eq} = 4\ \Omega
$$

The total current is:

$$
I = \frac{V}{R} = \frac{12}{4} = 3\ A
$$
```

## Exercise 3

Explain in your own words why adding branches in parallel makes equivalent resistance smaller.

*Exercise 3 image: adding branches creates more possible current paths.*

```{kroki}
:type: ditaa
:align: center

                  /---+----------+---\
+---------+---+  |   | Branch A |   |  +--------+
| Battery |   +--+   +----------+   +--+ Return |
+---------+---+  |                    |  +--------+
                  |   +----------+   |
                  +---+ Branch B +---+
                  |   +----------+   |
                  |   +----------+   |
                  +---+ Branch C +---+
                      +----------+
```

```{admonition} Key idea
:class: dropdown

When branches are added in parallel, current has more possible paths. More paths mean less opposition to current, so the equivalent resistance decreases.
```
