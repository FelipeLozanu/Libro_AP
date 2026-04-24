---
name: teachbook-generate-mermaid-diagram
description: >
  Genera diagramas Mermaid para el libro: flowcharts, ER, UML, secuencias, etc.
  Mermaid es un lenguaje basado en texto que Jupyter Book renderiza como imágenes sin dependencias externas.
  Trigger phrases: "diagrama mermaid", "diagrama de flujo", "ER", "UML", "mermaid",
  "flowchart", "diagrama de clases", "diagrama entidad relación", "diagrama de secuencia",
  "diagrama de estados", "diagrama de gantt".
---

# Skill: Generar Diagramas Mermaid

## Qué es Mermaid

Mermaid es un lenguaje de texto para crear diagramas. Se escribe como texto y se renderiza como imagen. Jupyter Book lo soporta de forma nativa sin instalar nada extra.

## Limitación importante

> **Mermaid renderiza en HTML pero NO en PDF.** Si necesitas el diagrama en PDF, genera una imagen PNG del diagrama y úsala con `{image}`. Para contenido solo web, Mermaid es perfecto.

## Sintaxis MyST

````markdown
```{mermaid}
:align: center
:caption: Título del diagrama

graph TD
    A[Inicio] --> B[Proceso]
    B --> C[Fin]
```
````

## Plantillas por tipo de diagrama

### Flowchart (diagrama de flujo)

````markdown
```{mermaid}
:align: center
:caption: Flujo del método científico

graph TD
    A[Observación] --> B[Hipótesis]
    B --> C[Experimentación]
    C --> D{¿Resultados válidos?}
    D -->|Sí| E[Conclusión]
    D -->|No| B
```
````

Direcciones: `graph TD` (arriba→abajo), `graph LR` (izquierda→derecha), `graph RL`, `graph BT`.

### Diagrama ER (entidad-relación)

````markdown
```{mermaid}
:align: center
:caption: Modelo entidad-relación de un experimento

erDiagram
    EXPERIMENTO ||--o{ MEDICION : tiene
    EXPERIMENTO {
        string nombre
        date fecha
        string responsable
    }
    MEDICION {
        float valor
        string unidad
        datetime timestamp
    }
```
````

### Diagrama de clases (UML)

````markdown
```{mermaid}
:align: center
:caption: Jerarquía de clases para organismos

classDiagram
    class Organismo {
        +String nombre
        +String reino
        +clasificar()
    }
    class Animal {
        +String habitat
        +moverse()
    }
    class Planta {
        +String tipo
        +fotosintesis()
    }
    Organismo <|-- Animal
    Organismo <|-- Planta
```
````

### Diagrama de secuencia

````markdown
```{mermaid}
:align: center
:caption: Proceso de obtención de resultados

sequenceDiagram
    participant E as Estudiante
    participant L as Laboratorio
    participant P as Profesor
    E->>L: Enviar muestra
    L->>L: Analizar muestra
    L-->>P: Enviar resultados
    P-->>E: Devolver informe
```
````

### Diagrama de estados

````markdown
```{mermaid}
:align: center
:caption: Ciclo del agua

stateDiagram-v2
    [*] --> Liquido
    Liquido --> Gas : Evaporación
    Gas --> Liquido : Condensación
    Liquido --> Solido : Congelación
    Solido --> Liquido : Fusión
```
````

### Diagrama de Gantt

````markdown
```{mermaid}
:align: center
:caption: Planificación del proyecto

gantt
    title Cronograma del experimento
    dateFormat  YYYY-MM-DD
    section Preparación
    Diseño experimental   :a1, 2025-01-01, 7d
    Recopilar material    :a2, after a1, 3d
    section Ejecución
    Realizar mediciones   :a3, after a2, 14d
    section Análisis
    Procesar datos        :a4, after a3, 7d
```
````

## Reglas

| Regla | Detalle |
|---|---|
| Simplicidad | Máximo **10-15 nodos**. Si necesitas más, divide en varios diagramas. |
| Etiquetas | Usar **español** para los textos (salvo que el contenido sea en inglés). |
| Caption | Siempre añadir `:caption:` descriptivo. |
| Alineación | Usar `:align: center` por defecto. |
| HTML vs PDF | Avisar al usuario que el diagrama **no aparecerá en PDF**. |
| Validación | Verificar la sintaxis Mermaid antes de insertar. Un error de sintaxis rompe la página. |

## Flujo de trabajo

1. Preguntar qué tipo de diagrama necesita el usuario y qué concepto quiere representar.
2. Elegir la plantilla adecuada del listado anterior.
3. Adaptar el contenido al caso concreto (nodos, etiquetas, relaciones).
4. Insertar en el archivo `.md` correspondiente usando ` ```{mermaid} `.
5. Avisar de la limitación con PDF.
