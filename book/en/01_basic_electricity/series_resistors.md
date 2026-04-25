# Series Resistors

In a series connection, current passes through one resistor and then the next one, with no alternative path.

*Simple diagram of three resistors connected in series.*

```{kroki}
:type: ditaa
:align: center

+---------+---+-----------+---+-----------+---+-----------+
| Battery |   |    R1     |   |    R2     |   |    R3     |
+---------+---+-----------+---+-----------+---+-----------+
```

## Basic rule

$$
R_{eq} = R_1 + R_2 + R_3 + \dots
$$

## Exercise 1

Three resistors of $2\ \Omega$, $3\ \Omega$, and $5\ \Omega$ are connected in series.

*Exercise 1 image: series circuit with 2 ohm, 3 ohm, and 5 ohm resistors.*

```{kroki}
:type: ditaa
:align: center

+--------------+---+----------+---+----------+---+----------+
| Battery 10 V |   | R1: 2 ohm|   | R2: 3 ohm|   | R3: 5 ohm|
+--------------+---+----------+---+----------+---+----------+
```

1. Calculate the equivalent resistance.
2. If the battery is $10\ V$, calculate the total current.

```{admonition} Solution
:class: dropdown

First, add the resistors:

$$
R_{eq} = 2 + 3 + 5 = 10\ \Omega
$$

Now apply Ohm's law:

$$
I = \frac{V}{R} = \frac{10}{10} = 1\ A
$$

Answer: the equivalent resistance is $10\ \Omega$ and the total current is $1\ A$.
```

## Exercise 2

In a series circuit there are two equal resistors of $6\ \Omega$ and a $12\ V$ battery.

*Exercise 2 image: two equal 6 ohm resistors in series connected to a 12 V battery.*

```{kroki}
:type: ditaa
:align: center

+--------------+---+----------+---+----------+
| Battery 12 V |   | R1: 6 ohm|   | R2: 6 ohm|
+--------------+---+----------+---+----------+
```

1. Find the equivalent resistance.
2. Calculate the current.
3. Calculate the voltage drop across each resistor.

```{admonition} Solution
:class: dropdown

The equivalent resistance is:

$$
R_{eq} = 6 + 6 = 12\ \Omega
$$

The total current is:

$$
I = \frac{12}{12} = 1\ A
$$

The voltage drop across each resistor is:

$$
V = I \cdot R = 1 \cdot 6 = 6\ V
$$
```

## Exercise 3

Design a series circuit with three resistors whose equivalent resistance is $15\ \Omega$. Write one possible combination and explain why it works.

*Exercise 3 image: one possible series combination of 4 ohm, 5 ohm, and 6 ohm.*

```{kroki}
:type: ditaa
:align: center

+---------+---+----------+---+----------+---+----------+
| Battery |   | R1: 4 ohm|   | R2: 5 ohm|   | R3: 6 ohm|
+---------+---+----------+---+----------+---+----------+
```

```{admonition} Possible answer
:class: dropdown

One option is $4\ \Omega$, $5\ \Omega$, and $6\ \Omega$.

$$
4 + 5 + 6 = 15\ \Omega
$$

It works because in series the equivalent resistance is the direct sum.
```
