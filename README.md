# 📘 MANUAL COMPLETO DE GITHUB ACTIONS  
## De Principiante a Avanzado (CI/CD, Data, Cloud y MLOps)

---

## 🧩 CAPÍTULO 1 – ¿QUÉ ES GITHUB ACTIONS?

### ✅ ¿Para qué sirve? 

GitHub Actions es una plataforma de automatización integrada en GitHub que te permite:

- Compilar código  
- Ejecutar tests  
- Validar calidad  
- Construir imágenes Docker  
- Desplegar a producción  
- Automatizar flujos de datos y ML  

👉 **En pocas palabras: automatiza TODO lo que hoy haces manualmente.**

---

## 🧱 CAPÍTULO 2 – CONCEPTOS FUNDAMENTALES

### 🔹 1. Workflow
Archivo YAML que define el proceso automático.  
Ubicación:
```bash
.github/workflows/nombre.yml
```
### 🔹 2. Job

Grupo de tareas que se ejecutan en una misma máquina.

### 🔹 3. Step
Cada instrucción dentro de un Job.

---

### 🔹 4. Runner
Servidor donde se ejecuta el workflow:

- `ubuntu-latest`  
- `windows-latest`  
- `macos-latest`  
- `self-hosted`  

---

### 🔹 5. Action
Bloque reutilizable creado por GitHub o la comunidad.

## 🏗 CAPÍTULO 3 – CREAR TU PRIMER WORKFLOW

### 🧪 Paso 1: Estructura del repositorio

En tu repo crea:

```bash
.github/
  workflows/
    primer-workflow.yml
```
### 🧪 Paso 2: Workflow mínimo

```yaml
name: Mi Primer Workflow

on: [push]

jobs:
  saludo:
    runs-on: ubuntu-latest
    steps:
      - name: Clonar repositorio
        uses: actions/checkout@v4

      - name: Mostrar mensaje
        run: echo "Hola Paquito, GitHub Actions funciona!"
## ⚡ CAPÍTULO 4 – EVENTOS (TRIGGERS)

Los *triggers* definen **cuándo se ejecuta tu workflow**.

---

### 🔹 Ejecutar al hacer push

```yaml
on: push
```
### 🔹 En Pull Requests

```yaml
on: pull_request
```
### 🔹 Manual (botón "Run workflow")

Permite ejecutar el workflow manualmente desde la interfaz de GitHub.

```yaml
on: workflow_dispatch
```

### 🔹 Programado (cron)

```yaml
on:
  schedule:
    - cron: '0 2 * * *'   # todos los días a las 2am
```
# 🧠 CAPÍTULO 5 – VARIABLES Y SECRETOS (GitHub Actions)

En este capítulo aprenderás a usar **variables de entorno (`env`)** y **secrets** para configurar y proteger tus workflows en GitHub Actions sin exponer información sensible.

---

## 🔐 1. Variables de entorno (`env`)

Las variables de entorno se usan para **configuración**, como entornos, nombres de proyectos, regiones, etc.

### 📌 Definir variables

```yaml
env:
  APP_ENV: production
```

## 🔐 2. Secrets (credenciales)

GitHub → Repo → Settings → Secrets → Actions → New secret

```yaml
run: echo "${{ secrets.AZURE_CLIENT_ID }}"
```

# 🧪 CAPÍTULO 6 – EJECUTAR CÓDIGO REAL (PYTHON)

En este capítulo ejecutamos **código Python real** dentro de GitHub Actions usando un pipeline de **CI (Integración Continua)** que instala dependencias y corre pruebas automáticamente en cada `push`.

---

## 🐍 Workflow para Python (CI)

```yaml
name: CI Python

on: [push]

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Instalar Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.10'

      - name: Instalar dependencias
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt

      - name: Ejecutar tests
        run: pytest
```
# 📦 CAPÍTULO 9 – ARTEFACTOS (SUBIR / BAJAR ARCHIVOS)

En este capítulo aprenderás a **guardar archivos generados en un job** y **recuperarlos en otro job** usando **Artifacts** en GitHub Actions.  
Esto es muy útil para reportes, resultados de tests, archivos compilados, modelos, logs, etc.

---

## 🔼 Subir archivos (Upload Artifact)

```yaml
- uses: actions/upload-artifact@v4
  with:
    name: resultados
    path: output/
```
## 🔽 Descargar archivos

```yaml
- uses: actions/download-artifact@v4
  with:
    name: resultados
```

