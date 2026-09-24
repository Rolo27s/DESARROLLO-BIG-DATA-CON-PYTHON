# Desarrollo de Big Data con Python

Material de apoyo para el curso de Python, Big Data e Inteligencia Artificial
impartido por Iván Palomares Carrascosa.

## Dataset

Durante el curso se utiliza la colección de datasets disponible en:

[gakudo-ai/open-datasets](https://github.com/gakudo-ai/open-datasets)

## Puesta en marcha

Los siguientes pasos están pensados para Windows y PowerShell.

### 1. Crear el entorno virtual

```powershell
py -m venv .venv
```

### 2. Permitir la ejecución de scripts en la sesión actual

Si PowerShell bloquea la activación del entorno, ejecuta:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

### 3. Activar el entorno virtual

```powershell
.\.venv\Scripts\Activate.ps1
```

Cuando el entorno esté activo, aparecerá `(.venv)` al inicio de la línea de
comandos.

### 4. Instalar las dependencias

El archivo `requirements.txt` contiene las versiones exactas de las
dependencias utilizadas en este proyecto. Para reproducir el mismo entorno:

```powershell
python -m pip install -r requirements.txt
```

### 5. Salir del entorno virtual

Cuando termines de trabajar, puedes desactivarlo con:

```powershell
deactivate
```
