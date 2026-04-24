---
name: teachbook-add-content
description: >
  Guía paso a paso para añadir nuevos capítulos o secciones al libro.
  Garantiza que el contenido se crea en TODOS los idiomas y que los TOC se mantienen sincronizados.
  Es la skill MÁS CRÍTICA del proyecto: un error aquí rompe la estructura multi-idioma.
  Trigger phrases: "añadir capítulo", "nueva sección", "nuevo contenido", "agregar contenido",
  "add chapter", "add content", "nueva página", "crear sección", "nuevo apartado",
  "añadir grado", "nuevo ejemplo".
---

# Skill: Añadir Contenido (Capítulos y Secciones)

## REGLA OBLIGATORIA

> Todo contenido debe existir en **TODOS los idiomas** configurados. Si se añade un archivo en español, DEBE existir el equivalente en inglés (y viceversa). Los cambios de contenido + TOC deben ir en el mismo commit.

## Proceso paso a paso

### Paso 1: Identificar qué se va a añadir

Determinar ANTES de escribir nada:
- ¿Es un **capítulo nuevo** (entrada directa en `chapters:`) o una **sección** dentro de un capítulo existente (entrada en `sections:`)?
- ¿En qué **parte** del TOC va? (Tutorial, Ejemplos por Grado, Información...)
- ¿Cuál es el **nombre del archivo** y la **ruta** en cada idioma?

### Paso 2: Crear los archivos de contenido en TODOS los idiomas

Los archivos se crean SIN la extensión `.md` en el TOC, pero el archivo físico SÍ la lleva.

**Ejemplo: Añadir "Grado Biología"**

Crear el directorio y archivos en español:
```
book/es/02_grados/grado_biologia/intro.md
book/es/02_grados/grado_biologia/ejemplo_biologia.md
```

Crear el directorio y archivos en inglés:
```
book/en/02_degrees/biology_degree/intro.md
book/en/02_degrees/biology_degree/biology_example.md
```

**Si la traducción no está lista aún**, crear el archivo con:
```markdown
*(Traducción pendiente)*
```

### Paso 3: Actualizar TODOS los `_toc_<lang>.yml`

**Los cambios deben ser IDÉNTICOS en estructura** en todos los idiomas (mismo orden, mismas secciones).

#### `_toc_es.yml` — Añadir dentro de la parte "Ejemplos por Grado":

```yaml
  - caption: Ejemplos por Grado
    chapters:
    - file: es/02_grados/grado_fisica/intro
      sections:
      - file: es/02_grados/grado_fisica/ejemplo_fisica
    - file: es/02_grados/grado_matematicas/intro
      sections:
      - file: es/02_grados/grado_matematicas/ejemplo_matematicas
    - file: es/02_grados/grado_estadistica/intro
      sections:
      - file: es/02_grados/grado_estadistica/ejemplo_estadistica
    - file: es/02_grados/grado_biologia/intro        # ← NUEVO
      sections:
      - file: es/02_grados/grado_biologia/ejemplo_biologia  # ← NUEVO
```

#### `_toc_en.yml` — Mismo cambio, rutas en inglés:

```yaml
  - caption: Examples by Degree
    chapters:
    - file: en/02_degrees/physics_degree/intro
      sections:
      - file: en/02_degrees/physics_degree/physics_example
    - file: en/02_degrees/math_degree/intro
      sections:
      - file: en/02_degrees/math_degree/math_example
    - file: en/02_degrees/stats_degree/intro
      sections:
      - file: en/02_degrees/stats_degree/stats_example
    - file: en/02_degrees/biology_degree/intro        # ← NUEVO
      sections:
      - file: en/02_degrees/biology_degree/biology_example  # ← NUEVO
```

### Reglas de formato del TOC

| Regla | Detalle |
|---|---|
| Indentación | **2 espacios** por nivel (NUNCA tabs) |
| Capítulos | `- file: ruta/sin/extension` (sin `.md`) |
| Secciones | Debajo del capítulo, con `sections:` y luego `- file: ...` |
| `root` | Solo el archivo raíz del libro (ej: `es/intro`) |
| Orden | Los idiomas deben tener la MISMA estructura en el MISMO orden |

### Paso 4: Verificar integridad

El agente DEBE ejecutar estas verificaciones ANTES de commit:

1. **Listar archivos `.md`** en `book/es/` y `book/en/` y confirmar que cada uno aparece en su `_toc_<lang>.yml`.
2. **Leer cada `_toc_<lang>.yml`** y confirmar que cada entrada `file:` apunta a un archivo que existe físicamente.
3. **Comparar la estructura** de ambos TOC: deben tener el mismo número de partes, capítulos y secciones.
4. **Reportar** cualquier archivo huérfano (existe pero no está en el TOC) o entrada rota (en el TOC pero no existe el archivo).

### Paso 5: Compilar para verificar

El agente DEBE usar el Python del entorno virtual (`.venv`):

| Sistema | Comando |
|---|---|
| Linux / macOS | `.venv/bin/python scripts/build_book.py` |
| Windows | `.venv\Scripts\python.exe scripts/build_book.py` |

Si la compilación falla, revisar los errores y corregir antes de continuar.

### Paso 6: Commitear todo junto

Los cambios de contenido (archivos `.md`) + cambios de estructura (`_toc_*.yml`) deben ir en el **mismo commit**.

## Para añadir un nuevo idioma

Si se necesita un idioma completamente nuevo (ej: portugués `pt`):

1. Crear `book/_config_pt.yml` (copiar de `_config_es.yml` y adaptar).
2. Crear `book/_toc_pt.yml` (misma estructura que `_toc_es.yml`).
3. Crear `book/pt/` con TODO el contenido traducido (misma estructura de carpetas).
4. Crear `latex_templates/pt/language_support.tex` si se quiere PDF.
5. Añadir `"pt": "Português"` al mapa `LANG_DISPLAY_NAMES` en `scripts/build_book.py`.
