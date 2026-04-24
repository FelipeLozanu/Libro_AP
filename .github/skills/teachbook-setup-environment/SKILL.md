---
name: teachbook-setup-environment
description: >
  Prepara el entorno completo desde cero: detecta/instala Python, git, uv,
  crea el entorno virtual, instala dependencias y sincroniza skills.
  CRÍTICO: usar la primera vez que se abre el proyecto en cualquier ordenador.
  Trigger phrases: "prepara el entorno", "instala todo", "configura el proyecto",
  "setup", "primera vez", "no me funciona", "falta algo", "no compila",
  "ModuleNotFoundError", "command not found", "no tengo python", "no tengo git".
---

# Skill: Preparar Entorno Completo (Desde Cero)

## Cuándo usar esta skill

- Es la **primera vez** que se abre el proyecto en este ordenador.
- Algo no funciona (`ModuleNotFoundError`, `command not found`, errores raros).
- Se ha cambiado de ordenador o se ha clonado el repositorio de nuevo.
- Se han añadido dependencias nuevas a `requirements.txt`.
- El usuario dice: "no tengo python", "no me compila", "falta algo".

---

## Paso 0: Diagnóstico del sistema

**OBLIGATORIO.** El agente DEBE ejecutar estos checks ANTES de hacer cualquier otra cosa:

```
Paso 0: Diagnóstico del sistema
┌─────────────────────────────────────────────────────────────────┐
│  El agente DEBE ejecutar estos comandos y anotar resultados:    │
│                                                                  │
│  Check 1: Python  →  python --version    (o py --version en Windows) │
│  Check 2: git     →  git --version                                │
│  Check 3: uv      →  uv --version                                 │
│  Check 4: .venv   →  ¿Existe la carpeta .venv/?                   │
└─────────────────────────────────────────────────────────────────┘
```

Ejecutar estos cuatro comandos y guardar los resultados. Según lo que falte, ir al paso correspondiente.

---

## Paso 1: Instalar lo que falte

### Escenario A: No hay Python

**macOS:**
```bash
# Si tiene Homebrew:
brew install python@3.12

# Si no tiene Homebrew, descargar de https://python.org
# O instalar uv primero (ver Escenario C) y luego: uv python install 3.12
```

**Windows:**
1. Descargar desde https://python.org
2. **CRÍTICO**: Marcar "Add Python to PATH" durante la instalación
3. Verificar abriendo una NUEVA terminal: `py --version`
4. Si `py` funciona pero `python` no, usar `py` en todos los comandos

**Linux (Ubuntu/Debian):**
```bash
sudo apt update && sudo apt install python3 python3-venv python3-pip
```

**Alternativa universal (si se instala uv primero):**
```bash
uv python install 3.12    # uv descarga y gestiona Python automáticamente
```

### Escenario B: No hay git

**macOS:**
```bash
xcode-select --install    # Instala herramientas de línea de comandos (incluye git)
# O: brew install git
```

**Windows:**
- Descargar desde https://git-scm.com

**Linux (Ubuntu/Debian):**
```bash
sudo apt install git
```

### Escenario C: No hay uv (pero Python ya existe)

uv es **muy recomendable** — 10-100x más rápido que pip y puede gestionar versiones de Python.

**Windows PowerShell:**
```powershell
irm https://astral.sh/uv/install.ps1 | iex
```

**macOS / Linux:**
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

**Después de instalar uv, recargar el PATH:**
- macOS/Linux: `source ~/.zshrc` (o `source ~/.bashrc` si usa bash)
- O cerrar y reabrir la terminal
- Windows: cerrar y reabrir la terminal

### Escenario D: Python es demasiado antiguo (< 3.10)

**Si uv está disponible:**
```bash
uv python install 3.12    # uv descarga Python 3.12 automáticamente
```

**Si no:**
- Descargar Python 3.12+ desde https://python.org

---

## Paso 2: Ejecutar setup_env.py

Solo después de que los prerrequisitos estén cubiertos (Python 3.10+ disponible):

| Situación | Comando |
|---|---|
| Python disponible, `.venv` no existe | `python scripts/setup_env.py` (o `py scripts/setup_env.py` en Windows) |
| uv disponible, `.venv` no existe | `uv run --python 3.12 scripts/setup_env.py` |
| `.venv` ya existe | NO ejecutar setup. Usar el Python del venv directamente |
| Solo sincronizar skills (venv ya existe) | `python scripts/setup_env.py --sync-only` |
| Modo desarrollo (con herramientas de test) | `python scripts/setup_env.py --dev` |

El script hace todo automáticamente:
1. Verifica versión de Python
2. Crea `.venv/`
3. Instala dependencias con uv (preferido) o pip (fallback)
4. Verifica paquetes clave
5. Sincroniza skills a `.claude/skills/`, `.agents/skills/`, `.agent/skills/`
6. Sincroniza `AGENTS.md` a `.github/copilot-instructions.md`
7. Muestra resumen final con el estado de todo

---

## Paso 3: Verificación final

Después del setup, el agente DEBE verificar que todo está bien:

```bash
# 1. El venv existe y tiene Python correcto
.venv/bin/python --version          # Linux/macOS
.venv\Scripts\python.exe --version  # Windows

# 2. jupyter-book está instalado
.venv/bin/python -c "import jupyter_book; print('OK')"          # Linux/macOS
.venv\Scripts\python.exe -c "import jupyter_book; print('OK')"  # Windows

# 3. Skills sincronizadas (carpetas existen)
ls .claude/skills/ .agents/skills/ .agent/skills/
```

Resultado esperado:
- ✅ Entorno listo — informar al usuario
- ❌ Si algo falla — consultar la tabla de troubleshooting

---

## Tabla de Troubleshooting Completa

| Problema | Causa | Solución |
|---|---|---|
| `python: command not found` (Linux/Mac) | Python no instalado o no en PATH | Instalar Python o usar `python3` en vez de `python` |
| `python: command not found` (Windows) | Python no instalado o no en PATH | Probar `py`. Si tampoco: instalar desde python.org marcando "Add to PATH" |
| `py: command not found` (Windows) | Python no instalado | Instalar desde python.org |
| `git: command not found` | Git no instalado | Instalar desde git-scm.com |
| `uv: command not found` después de instalar | Shell no recargó el PATH | Cerrar y reabrir la terminal. Mac/Linux: `source ~/.bashrc` o `source ~/.zshrc` |
| Error creating venv | Python no tiene venv (Linux) | `sudo apt install python3-venv` |
| Error de permisos | Usando sudo | NO usar sudo. Todo se instala en el directorio del usuario |
| `pip` falla con SSL | Certificados (macOS) | `/Applications/Python\ 3.12/Install\ Certificates.command` |
| Deps fallan al instalar | Falta compilador (Linux) | `sudo apt install build-essential python3-dev` |
| Windows: `Scripts` vs `bin` | Windows usa `Scripts\` | Usar `Scripts\python.exe` y `Scripts\pip.exe` |
| Windows: "cannot run scripts" | PowerShell execution policy | `Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned` |
| Python < 3.10 y no hay uv | Versión antigua | Instalar Python 3.12+ desde python.org |
| Python < 3.10 y hay uv | Versión antigua | `uv python install 3.12` (uv gestiona Python automáticamente) |

---

## Notas especiales por sistema operativo

### Windows
- Después de instalar Python, el PATH puede no actualizarse hasta reiniciar la terminal
- El launcher `py` es más fiable que `python` en Windows
- Si PowerShell bloquea scripts: `Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned`
- Rutas del venv usan `Scripts\` en vez de `bin/`

### macOS
- Después de instalar uv, recargar el shell: `source ~/.zshrc` (zsh) o `source ~/.bashrc` (bash)
- Si Python se instaló via brew: `brew install python@3.12`, usar `python3`
- Puede necesitar Xcode CLI: `xcode-select --install`
- Si pip falla por SSL: ejecutar `Install Certificates.command` en `/Applications/Python 3.12/`

### Linux
- Puede necesitar `python3-venv`: `sudo apt install python3-venv`
- Puede necesitar herramientas de compilación: `sudo apt install build-essential python3-dev`
- El comando puede ser `python3` en vez de `python`

---

## Después del setup

El entorno está listo. Siguiente paso: compilar el libro.

```bash
python scripts/build_book.py      # Compilar HTML multi-idioma
python scripts/preview_book.py    # Vista previa en localhost:8000
```
