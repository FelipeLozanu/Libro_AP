(videos)=
# Videos

Videos greatly enrich teaching materials. However, videos **cannot be embedded in PDF**, so you must always provide a text alternative.

## YouTube video (HTML + PDF)

ALWAYS use this dual pattern with `{raw} html` and `{raw} latex`:

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

Result:

```{raw} html
<iframe width="560" height="315" src="https://www.youtube.com/embed/dQw4w9WgXcQ" frameborder="0" allowfullscreen></iframe>
```

```{raw} latex
\begin{center}
\textbf{Video:} \url{https://www.youtube.com/watch?v=dQw4w9WgXcQ}
\end{center}
```

## How to get a YouTube video ID

1. Open the video in your browser.
2. The URL has this format: `https://www.youtube.com/watch?v=VIDEO_ID`
3. Use `VIDEO_ID` in the embed URL: `https://www.youtube.com/embed/VIDEO_ID`

For example, if the URL is `https://www.youtube.com/watch?v=abc123`, the iframe uses `https://www.youtube.com/embed/abc123`.

## Local video (HTML5)

For videos hosted in `_static/`:

````md
```{raw} html
<video width="560" controls>
  <source src="_static/my_video.mp4" type="video/mp4">
  Your browser does not support HTML5 video.
</video>
```

```{raw} latex
\begin{center}
\textbf{Local video:} see the digital version to play it.
\end{center}
```
````

Recommended path for local book videos:

- `book/_static/videos/my_video.mp4`

## Animation generated with Manim Community

If you want to create a mathematical or physics animation by code, use **Manim Community Edition** and save the result as an `.mp4` in `book/_static/videos/`.

Example scene:

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

Render command:

```bash
manim -pql wave.py SineWave
```

Embed it in the book:

````md
```{raw} html
<video width="720" controls>
  <source src="_static/videos/sine_wave.mp4" type="video/mp4">
  Your browser does not support HTML5 video.
</video>
```

```{raw} latex
\begin{center}
\textbf{Video: Animated sine wave.} See the HTML version of the book.
\end{center}
```
````

```{tip}
In this project use ONLY **Manim Community** (`from manim import *`). Do not use ManimGL.
```

## Video with description

It is good practice to add context before the video:

```md
The following video shows the crystallization process of copper sulfate:

[insert video block here]

Duration: 4:32 | Topic: Crystallization
```

## Recommended complete pattern

````md
The following video shows the experimental setup:

```{raw} html
<iframe width="560" height="315" src="https://www.youtube.com/embed/VIDEO_ID" frameborder="0" allowfullscreen></iframe>
```

```{raw} latex
\begin{center}
\textbf{Video: Experimental setup}\\
\url{https://www.youtube.com/watch?v=VIDEO_ID}
\end{center}
```

**Duration:** 5:15 | **Topic:** Chemical kinetics
````

```{warning}
NEVER use only `{raw} html` without the `{raw} latex` block. The PDF will contain no reference to the video and the reader will lose information.
```
