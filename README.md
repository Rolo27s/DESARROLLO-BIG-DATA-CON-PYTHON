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

### 5. Configurar Hadoop y `winutils` en Windows

PySpark necesita los binarios de Hadoop para algunas operaciones locales en
Windows. Clona el repositorio de `winutils` en la ruta esperada por los
notebooks:

```powershell
New-Item -ItemType Directory -Force C:\hadoop | Out-Null
git clone https://github.com/cdarlint/winutils.git C:\hadoop\winutils
```

Comprueba que existe la versión utilizada por este proyecto:

```powershell
Test-Path C:\hadoop\winutils\hadoop-3.3.6\bin\winutils.exe
```

El comando debe devolver `True`. Si la ruta o la versión disponibles en el
repositorio son diferentes, ajusta `HADOOP_HOME` para que apunte a la carpeta
que contiene `bin\winutils.exe`.

Antes de iniciar Spark, configura las variables de entorno en la sesión actual
de PowerShell:

```python
import os

os.environ["HADOOP_HOME"] = r"C:\hadoop\winutils\hadoop-3.3.6"
os.environ["hadoop.home.dir"] = os.environ["HADOOP_HOME"]
os.environ["PATH"] = os.path.join(
	os.environ["HADOOP_HOME"], "bin"
) + ";" + os.environ["PATH"]
```

En los notebooks del proyecto, esta configuración debe ejecutarse antes de
crear la `SparkSession`. Si se abre un terminal nuevo, hay que volver a
ejecutarla porque `os.environ` modifica únicamente el proceso de Python actual.

### 6. Salir del entorno virtual

Cuando termines de trabajar, puedes desactivarlo con:

```powershell
deactivate
```
