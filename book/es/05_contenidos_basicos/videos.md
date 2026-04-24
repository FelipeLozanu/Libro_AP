(videos)=
# Vídeos

Los vídeos enriquecen enormemente el material docente. Sin embargo, los vídeos **no se pueden incrustar en PDF**, así que es obligatorio proporcionar siempre una alternativa en texto.

## Vídeo de YouTube (HTML + PDF)

Usa SIEMPRE este patrón dual con `{raw} html` y `{raw} latex`:

````md
```{raw} html
<iframe width="560" height="315" src="https://www.youtube.com/embed/dQw4w9WgXcQ" frameborder="0" allowfullscreen></iframe>
```

```{raw} latex
\begin{center}
\textbf{Video:} \url{https://www.youtube.com/watch?v=dQw4w9WgXcQ}
\end{center}
```
````

Resultado:

```{raw} html
<iframe width="560" height="315" src="https://www.youtube.com/embed/dQw4w9WgXcQ" frameborder="0" allowfullscreen></iframe>
```

```{raw} latex
\begin{center}
\textbf{Video:} \url{https://www.youtube.com/watch?v=dQw4w9WgXcQ}
\end{center}
```

## Cómo obtener el ID de un vídeo de YouTube

1. Abre el vídeo en tu navegador.
2. La URL tiene este formato: `https://www.youtube.com/watch?v=VIDEO_ID`
3. Usa `VIDEO_ID` en la URL de incrustación: `https://www.youtube.com/embed/VIDEO_ID`

Por ejemplo, si la URL es `https://www.youtube.com/watch?v=abc123`, el iframe usa `https://www.youtube.com/embed/abc123`.

## Vídeo local (HTML5)

Para vídeos alojados en `_static/`:

````md
```{raw} html
<video width="560" controls>
  <source src="_static/mi_video.mp4" type="video/mp4">
  Tu navegador no soporta vídeo HTML5.
</video>
```

```{raw} latex
\begin{center}
\textbf{Video local:} consulte la versión digital para reproducirlo.
\end{center}
```
````

Ruta recomendada para los vídeos locales del libro:

- `book/_static/videos/mi_video.mp4`

## Animación generada con Manim Community

Si quieres crear una animación matemática o física por código, usa **Manim Community Edition** y guarda el resultado como `.mp4` en `book/_static/videos/`.

Ejemplo de escena:

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

Renderizado:

```bash
manim -pql wave.py SineWave
```

Inserción en el libro:

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

```{tip}
En este proyecto usa SOLO **Manim Community** (`from manim import *`). No uses ManimGL.
```

## Vídeo con descripción

Es buena práctica añadir contexto antes del vídeo:

```md
El siguiente vídeo muestra el proceso de cristalización del sulfato de cobre:

[insertar bloque de vídeo aquí]

Duración: 4:32 | Tema: Cristalización
```

## Patrón completo recomendado

````md
El siguiente vídeo muestra el montaje experimental:

```{raw} html
<iframe width="560" height="315" src="https://www.youtube.com/embed/VIDEO_ID" frameborder="0" allowfullscreen></iframe>
```

```{raw} latex
\begin{center}
\textbf{Video: Montaje experimental}\\
\url{https://www.youtube.com/watch?v=VIDEO_ID}
\end{center}
```

**Duración:** 5:15 | **Tema:** Cinética química
````

```{warning}
NUNCA uses solo `{raw} html` sin el bloque `{raw} latex`. El PDF no contendrá ninguna referencia al vídeo y el lector perderá información.
```
