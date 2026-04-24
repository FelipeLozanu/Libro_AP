---
name: teachbook-export-pdf
description: >
  Exporta el libro completo a formato PDF para cada idioma configurado.
  Genera LaTeX intermedio, aplica plantillas personalizadas y compila con Tectonic.
  Trigger phrases: "exportar PDF", "genera PDF", "PDF", "imprimible", "versión impresa",
  "quiero imprimir", "descargar PDF", "export pdf", "generate PDF".
---

# Skill: Exportar a PDF

## Cuándo usar esta skill

- Cuando se necesita una versión imprimible del libro.
- Para generar el archivo PDF que se descargará desde la web.
- Al finalizar el contenido y querer una copia offline.

## Qué hace `export_pdf.py`

1. **Verifica que LaTeX (Tectonic) esté instalado**. Si no, muestra instrucciones.
2. **Detecta los idiomas** desde los archivos `_config_<lang>.yml`.
3. **Para cada idioma**, genera los archivos LaTeX, aplica plantillas personalizadas y compila a PDF.
4. **Copia los PDFs** resultantes a `book/_static/`.

## Ubicación de salida

```
book/_static/teachbook_es.pdf    ← PDF en español
book/_static/teachbook_en.pdf    ← PDF en inglés
```

## Requisito previo: LaTeX (Tectonic)

El PDF requiere un motor LaTeX. El proyecto usa **Tectonic** (ligero, automático, no requiere instalación global de LaTeX).

### Verificar si Tectonic está instalado

```bash
tectonic --version
```

### Si NO está instalado, ejecutar PRIMERO:

El agente DEBE usar el Python del entorno virtual (`.venv`):

| Sistema | Comando |
|---|---|
| Linux / macOS | `.venv/bin/python scripts/setup_latex.py` |
| Windows | `.venv\Scripts\python.exe scripts/setup_latex.py` |

El script intenta instalar Tectonic primero vía pip, y si falla, descarga el binario directamente.

Para instalación silenciosa (sin prompt interactivo):
```bash
python scripts/setup_latex.py --yes
```

## Instrucciones para el agente

### Paso 1: Verificar Tectonic

Si Tectonic no está instalado, ejecutar `setup_latex.py` primero.

### Paso 2: Ejecutar la exportación

El agente DEBE usar el Python del entorno virtual (`.venv`):

| Sistema | Comando |
|---|---|
| Linux / macOS | `.venv/bin/python scripts/export_pdf.py` |
| Windows | `.venv\Scripts\python.exe scripts/export_pdf.py` |

## Personalización de plantillas LaTeX

Las plantillas están en `latex_templates/`:

```
latex_templates/
├── common/                    ← Estilos compartidos (jupyterBook.cls, etc.)
├── es/                        ← Ajustes para español (language_support.tex)
├── en/                        ← Ajustes para inglés
├── latexmkrc                  ← Configuración para latexmk
└── Makefile
```

- Los archivos de `common/` se aplican a TODOS los idiomas (capa base).
- Los archivos de `<lang>/` se aplican SOLO a ese idioma (capa de idioma, sobreescribe common).
- Los metadatos (título, autor, ISBN, editorial) se leen automáticamente de `_config_<lang>.yml` sección `latex:`.

## Solución de problemas

| Problema | Solución |
|---|---|
| "No se detectó un motor LaTeX" | Ejecutar `python scripts/setup_latex.py` primero |
| Error con videos de YouTube | Usar el patrón dual `{raw} html` + `{raw} latex` (ver skill `teachbook-multimedia`) |
| Error con imágenes SVG | Convertir a PNG; LaTeX no soporta SVG nativamente |
| Fórmulas mal renderizadas | Verificar que `dollarmath` está en `myst_enable_extensions` del config |
| Error "Font not found" | Tectonic descarga fuentes automáticamente; verificar conexión a internet |
| El PDF no tiene estilos personalizados | Verificar que `latex_templates/common/` contiene los archivos `.cls` y `.sty` |

## Flujo completo

```bash
# 1. Instalar LaTeX (solo la primera vez)
python scripts/setup_latex.py

# 2. Exportar PDFs para todos los idiomas
python scripts/export_pdf.py
```
