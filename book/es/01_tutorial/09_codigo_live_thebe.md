# 9. Código en Vivo con Thebe (Opcional)

**Thebe** es una tecnología que permite ejecutar código Python **directamente en el navegador** desde tu libro web. Los estudiantes pueden modificar el código y ver los resultados sin instalar nada.

```{warning}
Esta funcionalidad es **opcional** y requiere configuración adicional de un servidor Jupyter o Binder. No la necesitas para el funcionamiento básico de tu TeachBook.
```

## ¿Cómo funciona?

Thebe conecta tu libro web con un servidor Jupyter en la nube. Cuando el lector pulsa un botón "Run", el código se ejecuta en ese servidor y el resultado aparece en la página.

## Sintaxis: directiva `{code-cell}`

En lugar de un bloque de código normal, usas la directiva `{code-cell}`:

````md
```{code-cell} python
import numpy as np
print(np.sqrt(16))
```
````

Esto convierte el bloque de código en una celda ejecutable si Thebe está configurado.

## ¿Qué necesitas para activarlo?

1. Un servidor Jupyter accesible (puede ser [Binder](https://mybinder.org/) gratuito).
2. Configurar las opciones de Thebe en tu `_config.yml`.
3. Activar los botones de ejecución en la interfaz.

```{admonition} Nota
:class: tip
Si solo necesitas mostrar código estático con resaltado de sintaxis, usa bloques de código normales (`` ```python ``). Thebe solo es necesario si quieres que los lectores **ejecuten** el código.
```

## Alternativas más sencillas

Si Thebe te parece complejo, considera estas opciones:

- **Notebooks `.ipynb`**: Se ejecutan al compilar el libro (si activas `execute_notebooks: auto`).
- **HTML interactivo**: Usar `<details>` y CSS para simulaciones simples (ver capítulo anterior).
- **Enlaces a Google Colab**: Los lectores pueden abrir notebooks en la nube con un clic.

```{admonition} Resumen
Thebe es potente pero opcional. Empieza con contenido estático y notebooks, y considera Thebe cuando tus estudiantes necesiten experimentar con código en tiempo real.
```
