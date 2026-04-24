# 9. Live Code with Thebe (Optional)

**Thebe** is a technology that lets you run Python code **directly in the browser** from your web book. Students can modify the code and see results without installing anything.

```{warning}
This feature is **optional** and requires additional configuration of a Jupyter server or Binder. You do not need it for the basic TeachBook setup.
```

## How does it work?

Thebe connects your web book to a Jupyter server in the cloud. When the reader clicks a "Run" button, the code executes on that server and the result appears on the page.

## Syntax: the `{code-cell}` directive

Instead of a normal code block, use the `{code-cell}` directive:

````md
```{code-cell} python
import numpy as np
print(np.sqrt(16))
```
````

This turns the code block into an executable cell if Thebe is configured.

## What do you need to enable it?

1. An accessible Jupyter server (can be free [Binder](https://mybinder.org/)).
2. Configure Thebe options in your `_config.yml`.
3. Enable execution buttons in the interface.

```{admonition} Note
:class: tip
If you only need to display static code with syntax highlighting, use normal code blocks (`` ```python ``). Thebe is only necessary if you want readers to **execute** the code.
```

## Simpler alternatives

If Thebe seems too complex, consider these options:

- **`.ipynb` notebooks**: Executed when the book is built (if you enable `execute_notebooks: auto`).
- **Interactive HTML**: Use `<details>` and CSS for simple interactions (see previous chapter).
- **Google Colab links**: Readers can open notebooks in the cloud with one click.

```{admonition} Summary
Thebe is powerful but optional. Start with static content and notebooks, and consider Thebe when your students need to experiment with code in real time.
```
