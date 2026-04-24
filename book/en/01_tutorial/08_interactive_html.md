# 8. Interactive HTML in TeachBook

You can embed HTML directly into your TeachBook pages using the `{raw} html` directive. This lets you create interactive content **without needing JavaScript frameworks** like React or Vue.

## The `{raw} html` directive

Write the following in your `.md` file:

````md
```{raw} html
<your HTML here>
```
````

Everything inside is inserted as-is into the web page.

## Example: styled table

```{raw} html
<table style="border-collapse: collapse; width: 100%; margin: 1em 0;">
  <thead>
    <tr style="background: #2563eb; color: white;">
      <th style="padding: 10px; text-align: left;">Concept</th>
      <th style="padding: 10px; text-align: left;">Definition</th>
    </tr>
  </thead>
  <tbody>
    <tr style="border-bottom: 1px solid #e5e7eb;">
      <td style="padding: 10px;"><strong>TeachBook</strong></td>
      <td style="padding: 10px;">Interactive digital book based on Jupyter Book</td>
    </tr>
    <tr style="border-bottom: 1px solid #e5e7eb; background: #f9fafb;">
      <td style="padding: 10px;"><strong>MyST</strong></td>
      <td style="padding: 10px;">Markup language for scientific texts</td>
    </tr>
  </tbody>
</table>
```

## Example: collapsible content with `<details>`

```{raw} html
<details>
  <summary style="cursor: pointer; font-weight: bold; color: #2563eb;">
    Click to reveal the solution
  </summary>
  <div style="padding: 1em; border-left: 3px solid #2563eb; margin-top: 0.5em;">
    The derivative of $f(x) = x^2$ is $f'(x) = 2x$.
  </div>
</details>
```

This is perfect for hiding exercise solutions so students can reveal them when they are ready.

```{warning}
Content inserted with `{raw} html` **does not appear in the PDF export**. If you need content in the PDF, use standard MyST syntax (Markdown tables, `admonition` directives, etc.) instead.
```

```{admonition} Tip
:class: tip
Combine HTML for interactive elements (collapsibles, styling) with standard MyST for main content. This way your book works well in both web and PDF.
```
