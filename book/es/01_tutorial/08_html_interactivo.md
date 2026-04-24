# 8. HTML Interactivo en TeachBook

Puedes incrustar HTML directamente en las páginas de tu TeachBook usando la directiva `{raw} html`. Esto permite crear contenido interactivo **sin necesidad de frameworks JavaScript** como React o Vue.

## La directiva `{raw} html`

Escribe lo siguiente en tu archivo `.md`:

````md
```{raw} html
<tú HTML aquí>
```
````

Todo lo que pongas dentro se inserta tal cual en la página web.

## Ejemplo: tabla con estilo personalizado

```{raw} html
<table style="border-collapse: collapse; width: 100%; margin: 1em 0;">
  <thead>
    <tr style="background: #2563eb; color: white;">
      <th style="padding: 10px; text-align: left;">Concepto</th>
      <th style="padding: 10px; text-align: left;">Definición</th>
    </tr>
  </thead>
  <tbody>
    <tr style="border-bottom: 1px solid #e5e7eb;">
      <td style="padding: 10px;"><strong>TeachBook</strong></td>
      <td style="padding: 10px;">Libro digital interactivo basado en Jupyter Book</td>
    </tr>
    <tr style="border-bottom: 1px solid #e5e7eb; background: #f9fafb;">
      <td style="padding: 10px;"><strong>MyST</strong></td>
      <td style="padding: 10px;">Lenguaje de marcado para textos científicos</td>
    </tr>
  </tbody>
</table>
```

## Ejemplo: contenido desplegable con `<details>`

```{raw} html
<details>
  <summary style="cursor: pointer; font-weight: bold; color: #2563eb;">
    Haz clic para ver la solución
  </summary>
  <div style="padding: 1em; border-left: 3px solid #2563eb; margin-top: 0.5em;">
    La derivada de $f(x) = x^2$ es $f'(x) = 2x$.
  </div>
</details>
```

Esto es ideal para ocultar soluciones de ejercicios y que los estudiantes puedan revelarlas cuando estén listos.

```{warning}
El contenido HTML insertado con `{raw} html` **no aparece en la exportación PDF**. Si necesitas que el contenido esté en el PDF, usa sintaxis MyST estándar (tablas Markdown, directivas `admonition`, etc.) en su lugar.
```

```{admonition} Consejo
:class: tip
Combina HTML para lo interactivo (desplegables, estilo) con MyST estándar para el contenido principal. Así tu libro funciona bien tanto en web como en PDF.
```
