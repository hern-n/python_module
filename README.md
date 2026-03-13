# Plantilla de Módulo Python (pip)

Plantilla base para crear y publicar paquetes pip en Python.

## ¿Qué es pip?

**pip** es el gestor de paquetes oficial de Python. Permite instalar y gestionar bibliotecas y dependencias escritas en Python.

Con pip puedes:
- Instalar paquetes desde [PyPI](https://pypi.org/) (Python Package Index)
- Gestionar dependencias de tus proyectos
- Crear y publicar tus propios paquetes

## Estructura del Proyecto

```
python_module/
├── src/
│   └── new_module/      # Tu paquete Python
│       └── main.py      # Punto de entrada del módulo
├── pyproject.toml       # Configuración del paquete
├── README.md            # Este archivo
└── .gitignore           # Archivos ignorados por git
```

### Archivos principales

- **`pyproject.toml`**: Archivo de configuración que define el paquete (nombre, versión, dependencias, scripts, etc.)
- **`src/new_module/`**: Directorio principal del paquete (renombrar según necesidad)
- **`main.py`**: Código principal del módulo

## Instalación

### Requisitos previos

- Python 3.10 o superior
- pip actualizado

```bash
pip install --upgrade pip
```

### Instalar el paquete en modo desarrollo

Para desarrollar y probar el paquete localmente:

```bash
pip install -e .
```

Esto instala el paquete en "modo editable", permitiendo cambios sin reinstall.

### Crear la distribución

```bash
pip install build
python -m build
```

Esto genera los archivos `.whl` y `.tar.gz` en la carpeta `dist/`.

### Publicar en PyPI

```bash
pip install twine
twine upload dist/*
```

## Uso

Una vez instalado, puedes usar el comando definido en `pyproject.toml`:

```bash
command
```

O importar el módulo en Python:

```python
from new_module import main

main.main()
```

## Configuración

Edita `pyproject.toml` para personalizar:

- **name**: Nombre del paquete en PyPI
- **version**: Versión semántica
- **description**: Descripción breve
- **dependencies**: Librerías requeridas
- **scripts**: Comandos CLI disponibles

## Ejemplo de pyproject.toml

```toml
[build-system]
requires = ["setuptools", "wheel"]
build-backend = "setuptools.build_meta"

[project]
name = "mi_paquete"
version = "1.0.0"
description = "Una descripción de mi paquete"
readme = "README.md"
requires-python = ">=3.10"
dependencies = [
    "requests>=2.28.0",
]

[project.scripts]
mi-comando = "mi_paquete.main:main"

[tool.setuptools.packages.find]
where = ["src"]
```

## Recursos adicionales

- [Documentación de pip](https://pip.pypa.io/)
- [Guía de empaquetado Python](https://packaging.python.org/)
- [PyPI - Python Package Index](https://pypi.org/)