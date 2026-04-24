# Diagrama de Clases UML con Mermaid

Los diagramas de clases son esenciales para modelar sistemas orientados a objetos.
Mermaid permite representar clases con sus atributos, métodos y relaciones de herencia.

## Ejemplo: Jerarquía de Figuras Geométricas

```{mermaid}
classDiagram
    class Figura {
        <<abstract>>
        +String color
        +area() float
        +perimetro() float
    }

    class Circulo {
        +float radio
        +area() float
        +perimetro() float
    }

    class Rectangulo {
        +float ancho
        +float alto
        +area() float
        +perimetro() float
    }

    class Triangulo {
        +float base
        +float altura
        +area() float
        +perimetro() float
    }

    Figura <|-- Circulo
    Figura <|-- Rectangulo
    Figura <|-- Triangulo
```

## Notación de clases

- **Atributos**: Se listan en la primera sección. Prefija con `+` (público), `-` (privado), `#` (protegido).
- **Métodos**: Se listan en la segunda sección, con el tipo de retorno.
- **Clase abstracta**: Indicada con `<<abstract>>`.

## Tipos de relaciones

| Notación | Significado |
|----------|-------------|
| `<\|--` | Herencia (es un) |
| `*--` | Composición |
| `o--` | Agregación |
| `-->` | Asociación |
| `..>` | Dependencia |
