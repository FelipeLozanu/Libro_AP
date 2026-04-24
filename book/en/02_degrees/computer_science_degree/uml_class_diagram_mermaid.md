# UML Class Diagram with Mermaid

Class diagrams are essential for modeling object-oriented systems.
Mermaid allows you to represent classes with their attributes, methods, and inheritance relationships.

## Example: Geometric Shape Hierarchy

```{mermaid}
classDiagram
    class Shape {
        <<abstract>>
        +String color
        +area() float
        +perimeter() float
    }

    class Circle {
        +float radius
        +area() float
        +perimeter() float
    }

    class Rectangle {
        +float width
        +float height
        +area() float
        +perimeter() float
    }

    class Triangle {
        +float base
        +float height
        +area() float
        +perimeter() float
    }

    Shape <|-- Circle
    Shape <|-- Rectangle
    Shape <|-- Triangle
```

## Class notation

- **Attributes**: Listed in the first section. Prefix with `+` (public), `-` (private), `#` (protected).
- **Methods**: Listed in the second section, with return type.
- **Abstract class**: Indicated with `<<abstract>>`.

## Relationship types

| Notation | Meaning |
|----------|---------|
| `<\|--` | Inheritance (is a) |
| `*--` | Composition |
| `o--` | Aggregation |
| `-->` | Association |
| `..>` | Dependency |
