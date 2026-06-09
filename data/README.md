# Dataset

Esta carpeta contiene los scripts y la documentación necesaria para descargar y organizar el dataset utilizado en el proyecto **Blood Cell Deep Learning Comparison**.

## Fuente de datos

El proyecto utiliza un dataset de imágenes de células sanguíneas disponible en Kaggle.

La descarga se realiza mediante la Kaggle API, por lo que es necesario contar con una cuenta de Kaggle y un archivo de credenciales `kaggle.json`.

## Archivos de descarga

Esta carpeta incluye dos scripts:

```txt
download_data.sh
download_data.ps1
```

### `download_data.sh`

Script para Linux, macOS o WSL.

Ejemplo de ejecución:

```bash
bash download_data.sh
```

### `download_data.ps1`

Script para Windows PowerShell.

Ejemplo de ejecución:

```powershell
.\download_data.ps1
```

## Configuración de Kaggle API

Para descargar datasets desde Kaggle, se debe configurar el archivo `kaggle.json`.

Pasos generales:

1. Iniciar sesión en Kaggle.
2. Ir a la sección de cuenta.
3. Crear un nuevo API Token.
4. Descargar el archivo `kaggle.json`.
5. Ubicarlo en la ruta esperada por Kaggle.

En Windows normalmente se ubica en:

```txt
C:\Users\<usuario>\.kaggle\kaggle.json
```

En Linux o WSL normalmente se ubica en:

```txt
~/.kaggle/kaggle.json
```

El archivo `kaggle.json` no debe subirse al repositorio.

## Estructura esperada después de la descarga

Después de ejecutar el script de descarga, el dataset debe quedar organizado dentro de esta carpeta o en una subcarpeta similar a:

```txt
data/
  blood_cells/
    dataset2-master/
      dataset2-master/
        images/
          TRAIN/
          TEST/
```

La estructura exacta puede variar según cómo Kaggle entregue el archivo comprimido, pero el código del proyecto espera encontrar carpetas de entrenamiento y prueba.

## Estructura usada por el código

Las funciones de carga de datos esperan una estructura con carpetas por clase, por ejemplo:

```txt
images/
  TRAIN/
    EOSINOPHIL/
    LYMPHOCYTE/
    MONOCYTE/
    NEUTROPHIL/

  TEST/
    EOSINOPHIL/
    LYMPHOCYTE/
    MONOCYTE/
    NEUTROPHIL/
```

Cada subcarpeta representa una clase de célula sanguínea.

## Clases del dataset

El dataset contiene imágenes clasificadas en cuatro tipos principales de células sanguíneas:

| Clase | Descripción |
|---|---|
| `EOSINOPHIL` | Eosinófilos |
| `LYMPHOCYTE` | Linfocitos |
| `MONOCYTE` | Monocitos |
| `NEUTROPHIL` | Neutrófilos |

Estas clases son utilizadas para entrenar modelos de clasificación multiclase.

## Por qué no se sube el dataset

El dataset no se versiona en GitHub porque contiene muchas imágenes y puede aumentar considerablemente el peso del repositorio.

En su lugar:

- Se documenta la fuente.
- Se incluyen scripts de descarga.
- Se ignora la carpeta generada mediante `.gitignore`.

## Carpetas ignoradas

El `.gitignore` del proyecto excluye la carpeta donde se descarga el dataset:

```gitignore
data/blood_cells/
```

Esto evita subir datos pesados al repositorio.

## Uso en los notebooks

El dataset es utilizado principalmente en:

```txt
notebooks/01_eda.ipynb
notebooks/02_lenet_vgg.ipynb
notebooks/03_transfer_learning.ipynb
```

También es utilizado por las funciones reutilizables ubicadas en:

```txt
src/utils.py
src/train.py
```

## Recomendaciones

- Mantener el dataset fuera de GitHub.
- Verificar que las carpetas `TRAIN` y `TEST` existan después de la descarga.
- No subir `kaggle.json`.
- Ejecutar primero el notebook de EDA para validar la carga correcta.
- Usar rutas relativas al proyecto para mejorar reproducibilidad.

## Nota

Este dataset se utiliza únicamente con fines académicos y experimentales dentro del proyecto de clasificación de imágenes de células sanguíneas.
