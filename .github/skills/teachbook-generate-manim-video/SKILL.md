---
name: teachbook-generate-manim-video
description: >
  Genera animaciones educativas con Manim Community Edition y las integra como vídeos locales HTML5 en el libro.
  SOLO usa Manim Community (no ManimGL). Trigger phrases: "manim", "animación matemática",
  "video animado", "animación física", "animación geometría", "video local", "mp4".
license: Apache-2.0
metadata:
  author: gentleman-programming
  version: "1.0"
---

## Cuándo usar

- Cuando el usuario quiera una **animación matemática o física** generada por código
- Cuando quiera un **vídeo local** dentro del libro, no solo YouTube
- Cuando necesite una explicación visual paso a paso (funciones, vectores, geometría, señales)

## Patrón crítico del proyecto

### SOLO Manim Community

Usar exclusivamente:

```python
from manim import *
```

NO usar:
- `from manimlib import *`
- `manimgl`
- ejemplos o APIs de 3Blue1Brown / ManimGL

### Salida recomendada

El vídeo final debe quedar en una ruta estable dentro del libro, por ejemplo:

- `book/_static/videos/mi_animacion.mp4`

Luego se inserta con HTML5:

````md
```{raw} html
<video width="720" controls>
  <source src="_static/videos/mi_animacion.mp4" type="video/mp4">
  Tu navegador no soporta vídeo HTML5.
</video>
```

```{raw} latex
\begin{center}
\textbf{Vídeo:} consulte la versión HTML del libro para reproducir la animación.
\end{center}
```
````

## Flujo recomendado

1. Crear un archivo Python con una escena de Manim Community
2. Renderizarlo con `manim`
3. Copiar o mover el `.mp4` final a `book/_static/videos/`
4. Insertarlo con el patrón HTML + LaTeX fallback

## Ejemplo mínimo

Archivo `wave.py`:

```python
from manim import *
import numpy as np


class SineWave(Scene):
    def construct(self):
        axes = Axes(
            x_range=[0, 2 * np.pi, np.pi / 2],
            y_range=[-1.5, 1.5, 0.5],
            x_length=8,
            y_length=4,
        )
        curve = axes.plot(lambda x: np.sin(x), color=BLUE)
        label = MathTex("y = \\sin(x)").next_to(axes, UP)

        self.play(Create(axes))
        self.play(Create(curve), Write(label))
        self.wait(1)
```

Render:

```bash
manim -pql wave.py SineWave
```

## Inserción en MyST

````md
```{raw} html
<video width="720" controls>
  <source src="_static/videos/sine_wave.mp4" type="video/mp4">
  Tu navegador no soporta vídeo HTML5.
</video>
```

```{raw} latex
\begin{center}
\textbf{Vídeo: Onda senoidal animada.} Consulte la versión HTML del libro.
\end{center}
```
````

## Requisitos

- Python 3.10+
- FFmpeg instalado
- Manim Community instalado en el entorno que se use para renderizar

Ejemplo de instalación manual:

```bash
python -m pip install manim
manim --version
```

## Reglas

| Regla | Detalle |
|---|---|
| Framework | SOLO **Manim Community Edition** |
| Import | `from manim import *` |
| Salida | Guardar `.mp4` en `book/_static/videos/` |
| Inserción | Usar siempre patrón dual HTML + LaTeX fallback |
| Multi-idioma | Si se documenta una animación en una página nueva, replicarla en todos los idiomas |
| Simplicidad | Escenas cortas, claras y didácticas |

## Comandos

```bash
# Render rápido de baja calidad para probar
manim -pql archivo.py NombreDeLaEscena

# Render a calidad media
manim -pqm archivo.py NombreDeLaEscena
```
