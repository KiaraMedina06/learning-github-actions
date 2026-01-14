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


