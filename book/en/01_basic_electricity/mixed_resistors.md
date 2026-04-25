# Mixed Resistors

A mixed circuit combines series sections and parallel sections. The main idea is to simplify step by step.

*Simple diagram of a mixed circuit with one series resistor and two parallel branches.*

```{kroki}
:type: ditaa
:align: center

+---------+---+-----------------+---+-----------+
| Battery |   | Series resistor |   |  Return   |
+---------+---+-----------------+---+-----------+
				 |                         ^
				 |                         |
				 +---+-----------+---+-----+
				 |   | Branch 1  |   |
				 |   +-----------+   |
				 |   +-----------+   |
				 +---+ Branch 2  +---+
					 +-----------+
```

## Strategy

1. Identify which resistors are clearly in series or in parallel.
2. Replace that group with an equivalent resistor.
3. Repeat until only one resistor remains.

## Exercise 1

A $4\ \Omega$ resistor is in series with a parallel block made of $6\ \Omega$ and $3\ \Omega$.

*Exercise 1 image: a 4 ohm resistor in series with a parallel block of 6 ohm and 3 ohm.*

```{kroki}
:type: ditaa
:align: center

+---------+---+----------+---+--------+
| Battery |   | R1: 4 ohm|   | Return |
+---------+---+----------+---+--------+
				 |                ^
				 |                |
				 +---+----------+-+
				 |   | R2: 6 ohm| |
				 |   +----------+ |
				 |   +----------+ |
				 +---+ R3: 3 ohm+-+
					 +----------+
```

1. Calculate the equivalent resistance of the parallel block.
2. Calculate the total resistance of the circuit.

```{admonition} Solution
:class: dropdown

First solve the parallel block:

$$
\frac{1}{R_p} = \frac{1}{6} + \frac{1}{3} = \frac{1}{2}
$$

So:

$$
R_p = 2\ \Omega
$$

Now add the series resistor:

$$
R_{eq} = 4 + 2 = 6\ \Omega
$$
```

## Exercise 2

In a circuit there are two $8\ \Omega$ resistors in parallel and then a $4\ \Omega$ resistor in series.

*Exercise 2 image: two 8 ohm resistors in parallel followed by a 4 ohm series resistor with a 12 V battery.*

```{kroki}
:type: ditaa
:align: center

+--------------+      /---+----------+---\
| Battery 12 V |--+---+   | R1: 8 ohm|   +---+----------+---+--------+
+--------------+  |   |   +----------+   |   | R3: 4 ohm|   | Return |
                  |   +---+----------+---+   +----------+---+--------+
                  |       | R2: 8 ohm|
                  |       +----------+
```

1. Find the resistance of the parallel block.
2. Calculate the total resistance.
3. If the battery is $12\ V$, calculate the total current.

```{admonition} Solution
:class: dropdown

Two equal resistors in parallel are equivalent to half their value:

$$
R_p = 4\ \Omega
$$

The total resistance is:

$$
R_{eq} = 4 + 4 = 8\ \Omega
$$

The total current is:

$$
I = \frac{12}{8} = 1.5\ A
$$
```

## Exercise 3

Consider this verbal scheme: a $2\ \Omega$ resistor in series with two $4\ \Omega$ resistors in parallel, followed by another $2\ \Omega$ resistor in series.

*Exercise 3 image: mixed circuit with 2 ohm in series, a 4 ohm and 4 ohm parallel block, and another 2 ohm in series.*

```{kroki}
:type: ditaa
:align: center

+---------+---+----------+      /---+----------+---\
| Battery |   | R1: 2 ohm|--+---+   | R2: 4 ohm|   +---+----------+---+--------+
+---------+---+----------+  |   |   +----------+   |   | R4: 2 ohm|   | Return |
                            |   +---+----------+---+   +----------+---+--------+
                            |       | R3: 4 ohm|
                            |       +----------+
```

Calculate the total equivalent resistance.

```{admonition} Solution
:class: dropdown

The parallel block of $4\ \Omega$ and $4\ \Omega$ is:

$$
R_p = 2\ \Omega
$$

Then everything is in series:

$$
R_{eq} = 2 + 2 + 2 = 6\ \Omega
$$
```
