---
name: teachbook-multimedia
description: >
  Guía para insertar contenido multimedia en el libro: imágenes, videos de YouTube,
  ecuaciones LaTeX, tablas, admoniciones, código ejecutable y citas bibliográficas.
  Todos los patrones son compatibles con HTML y PDF simultáneamente.
  Trigger phrases: "insertar imagen", "añadir video", "YouTube", "fórmula", "ecuación",
  "tabla", "nota", "advertencia", "cita bibliográfica", "imagen", "multimedia",
  "insertar multimedia", "video", "BibTeX", "referencia", "add image", "add video".
---

# Skill: Contenido Multimedia (HTML + PDF)

## Regla fundamental

Todo contenido multimedia debe funcionar en **HTML** (web) y en **PDF** (imprimible). Los patrones de esta skill garantizan compatibilidad con ambos formatos.

---

## 1. Imágenes

**Compatibilidad: HTML ✅ PDF ✅**

```markdown
```{image} _static/mi_imagen.png
:alt: Descripción textual de la imagen
:width: 80%
:align: center
```
```

- Formatos recomendados: **PNG**, **JPG** o **SVG** (SVG solo en HTML; para PDF convertir a PNG).
- Ubicación: `book/_static/` (compartido) o junto al archivo `.md`.
- La ruta es relativa al archivo `.md` donde se inserta.

**Error común**: Usar sintaxis de imagen estándar `![alt](ruta)` — funciona en HTML pero puede dar problemas en PDF. Preferir siempre la directiva `{image}`.

---

## 2. Videos de YouTube

**Compatibilidad: HTML ✅ PDF ✅ (con patrón dual)**

Usar SIEMPRE este patrón dual. NUNCA usar iframe sin el bloque `{raw} latex` alternativo:

````markdown
```{raw} html
<iframe width="560" height="315" src="https://www.youtube.com/embed/VIDEO_ID" frameborder="0" allowfullscreen></iframe>
```

```{raw} latex
\begin{center}
\textbf{Video:} \url{https://www.youtube.com/watch?v=VIDEO_ID}
\end{center}
```
````

Reemplazar `VIDEO_ID` por el ID real del video (los caracteres después de `v=` en la URL).

- En **HTML**: se ve el video embebido con el reproductor de YouTube.
- En **PDF**: se ve un enlace de texto al video.

**Error crítico**: Usar `{raw} html` sin el bloque `{raw} latex`. Esto causa que el PDF falle o muestre contenido vacío.

---

## 3. Ecuaciones LaTeX

**Compatibilidad: HTML ✅ PDF ✅**

Ecuación inline:
```markdown
La energía se define como $E = mc^2$ en la teoría de la relatividad.
```

Ecuación display (bloque centrado):
```markdown
$$
\int_0^\infty e^{-x^2} dx = \frac{\sqrt{\pi}}{2}
$$
```

Requiere que `dollarmath` esté en `myst_enable_extensions` del `_config.yml` (ya configurado por defecto).

---

## 4. Tablas

**Compatibilidad: HTML ✅ PDF ✅**

```markdown
| Concepto | Fórmula | Unidad |
|---|---|---|
| Velocidad | $v = \dfrac{d}{t}$ | m/s |
| Fuerza | $F = ma$ | N |
| Energía | $E = mc^2$ | J |
```

- Usar al menos 3 guiones `---` en la fila separadora.
- Se pueden combinar con ecuaciones LaTeX inline dentro de las celdas.

---

## 5. Admoniciones (bloques destacados)

**Compatibilidad: HTML ✅ PDF ✅**

````markdown
```{note}
Este es un bloque de nota. Aparece con estilo diferenciado.
```

```{warning}
Este es un bloque de advertencia. Úsalo para avisos importantes.
```

```{tip}
Este es un consejo. Úsalo para recomendaciones útiles.
```

```{admonition} Título personalizado
Este bloque admite un título personalizado.
```
````

**Error común**: Olvidar cerrar el bloque con las tres comillas invertidas `` ``` ``.

---

## 6. Código ejecutable (Notebooks)

**Compatibilidad: HTML ✅ PDF ✅**

Los archivos `.ipynb` (Jupyter notebooks) se pueden colocar junto a los `.md`. Para que el código se ejecute automáticamente durante la compilación, el `_config_<lang>.yml` debe tener:

```yaml
execute:
  execute_notebooks: auto
```

Por defecto está en `off` para velocidad de compilación. Solo activar si el usuario lo pide explícitamente.

**Nota**: Los notebooks ejecutados pueden tardar mucho en compilar. Desaconsejar su uso salvo necesidad real.

---

## 7. Citas bibliográficas (BibTeX)

**Compatibilidad: HTML ✅ PDF ✅**

Archivo de referencias: `book/_static/references.bib`

Citar en el texto:
```markdown
Según {cite}`smith2023`, los resultados confirman la hipótesis.
```

Añadir la bibliografía al final de una página:
````markdown
```{bibliography}
```
````

Entrada de ejemplo en `references.bib`:
```bibtex
@article{smith2023,
  author  = {Smith, John},
  title   = {A Study on Something},
  journal = {Journal of Examples},
  year    = {2023},
  volume  = {1},
  pages   = {1--10}
}
```

---

## Resumen de compatibilidad

| Tipo | HTML | PDF | Notas |
|---|---|---|---|
| Imágenes (`{image}`) | ✅ | ✅ | PNG/JPG recomendado |
| YouTube (patrón dual) | ✅ | ✅ | NUNCA sin `{raw} latex` |
| Ecuaciones (`$...$`) | ✅ | ✅ | Requiere `dollarmath` en config |
| Tablas | ✅ | ✅ | Sintaxis MyST estándar |
| Admoniciones | ✅ | ✅ | `{note}`, `{warning}`, `{tip}`, `{admonition}` |
| Notebooks (`.ipynb`) | ✅ | ✅ | Desactivado por defecto |
| BibTeX (`{cite}`) | ✅ | ✅ | Archivo: `_static/references.bib` |
