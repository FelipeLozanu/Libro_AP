---
name: teachbook-live-preview
description: >
  Inicia un servidor local con previsualización en vivo del libro.
  Los cambios en archivos .md se detectan automáticamente y se recompilan al guardar.
  El navegador se abre automáticamente en el puerto 8000.
  Trigger phrases: "vista previa", "preview", "en vivo", "live", "quiero ver el libro",
  "abre el navegador", "servidor local", "hot reload", "ver cambios en tiempo real",
  "enséñame cómo queda", "previsualizar".
---

# Skill: Previsualización en Vivo (Live Preview)

## Cuándo usar esta skill

- Mientras se escribe contenido y se quiere ver cómo queda en tiempo real.
- Para corregir formato, imágenes o fórmulas viendo el resultado al instante.
- Para trabajar de forma iterativa sin tener que compilar manualmente cada vez.

## Qué hace `preview_book.py`

1. **Ejecuta una compilación completa inicial** (llama a `build_book.py` internamente). Esto puede tardar 1-2 minutos la primera vez.
2. **Genera la configuración Sphinx** (`conf.py`) para compatibilidad con `sphinx-autobuild`.
3. **Inicia un watcher** que vigila cambios en `_config.yml` para regenerar la configuración al vuelo.
4. **Arranca `sphinx-autobuild`** en el puerto 8000 con detección de cambios automática.
5. **Abre el navegador** automáticamente en `http://localhost:8000`.

## Instrucciones para el agente

### Ejecutar la previsualización

El agente DEBE usar el Python del entorno virtual (`.venv`):

| Sistema | Comando |
|---|---|
| Linux / macOS | `.venv/bin/python scripts/preview_book.py` |
| Windows | `.venv\Scripts\python.exe scripts/preview_book.py` |

### IMPORTANTE: Este proceso es de larga duración

- El script se queda ejecutando en primer plano hasta que el usuario lo detenga.
- NO ejecutar este script y esperar que termine — es un servidor que se mantiene activo.
- Si se ejecuta desde un agente CLI, informar al usuario que el servidor está corriendo.

### Para detener el servidor

- Pulsar `Ctrl+C` en la terminal donde se ejecuta.
- El script captura `KeyboardInterrupt` y limpia los recursos correctamente.

## Comportamiento del hot-reload

| Archivo modificado | Qué ocurre |
|---|---|
| `book/es/*.md`, `book/en/*.md` | Sphinx recompila automáticamente la página afectada |
| `book/_config_es.yml` u otro config | El watcher regenera `conf.py` y se recompila |
| `book/_static/*` (CSS, JS, imágenes) | Se requiere recarga manual del navegador |

## Notas importantes

- La **primera ejecución** tarda más porque compila TODO el libro completo.
- Las **ediciones posteriores** son rápidas: solo se recompilan las páginas modificadas.
- El servidor está disponible en `http://localhost:8000` mientras el proceso esté activo.
- Si el puerto 8000 está ocupado, se debe detener el proceso anterior primero.
