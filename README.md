# Blood Cell Deep Learning Comparison

Blood Cell Deep Learning Comparison es un proyecto académico de Deep Learning aplicado a clasificación de imágenes de células sanguíneas. El proyecto compara distintos enfoques de redes neuronales convolucionales, incluyendo modelos CNN base, uso de Batch Normalization y Transfer Learning con ResNet18.

El trabajo fue desarrollado como parte de una actividad académica de Deep Learning, con el objetivo de evaluar cómo diferentes arquitecturas y técnicas de entrenamiento afectan el rendimiento de un modelo de clasificación de imágenes.

## Objetivo del proyecto

El objetivo principal es comparar el desempeño de diferentes modelos de clasificación de imágenes aplicados a un dataset de células sanguíneas.

El proyecto busca demostrar:

- Exploración inicial del dataset.
- Preparación de datos para clasificación de imágenes.
- Entrenamiento de modelos CNN.
- Comparación entre una arquitectura tipo LeNet y una arquitectura tipo VGG.
- Evaluación del impacto de Batch Normalization.
- Análisis del learning rate.
- Aplicación de Transfer Learning con ResNet18.
- Registro de métricas y visualizaciones de resultados.

## Tecnologías utilizadas

- Python
- PyTorch
- Torchvision
- NumPy
- Pandas
- Matplotlib
- Scikit-learn
- Jupyter Notebook
- Kaggle API

## Dataset

El proyecto utiliza un dataset de imágenes de células sanguíneas descargado desde Kaggle.

El dataset no se sube directamente al repositorio para evitar archivos pesados. En su lugar, se incluyen scripts de descarga en la carpeta `data/`.

Para más detalle sobre la estructura esperada del dataset, revisar:

[`data/README.md`](data/README.md)

## Estructura del proyecto

```txt
Blood-Cell-Deep-Learning-Comparison/
  README.md
  requirements.txt
  .gitignore

  data/
    README.md
    download_data.ps1
    download_data.sh

  docs/
    final_report.pdf
    methodology.md

  notebooks/
    00_colab_reproducible.ipynb
    01_eda.ipynb
    02_lenet_vgg.ipynb
    03_transfer_learning.ipynb

  results/
    checkpoints/
      .gitkeep
    figures/
    metrics/

  src/
    models.py
    train.py
    utils.py
```

## Descripción de carpetas

### `data/`

Contiene scripts para descargar el dataset y documentación sobre su estructura esperada.

Archivos principales:

- `download_data.sh`: script de descarga para Linux, macOS o WSL.
- `download_data.ps1`: script de descarga para Windows PowerShell.
- `README.md`: explicación de la fuente de datos, descarga y organización esperada.

### `docs/`

Contiene documentación del proyecto.

- `final_report.pdf`: informe académico final.
- `methodology.md`: explicación metodológica del análisis, entrenamiento y comparación de modelos.

### `notebooks/`

Contiene los notebooks principales del proyecto.

- `00_colab_reproducible.ipynb`: versión reproducible para Google Colab.
- `01_eda.ipynb`: análisis exploratorio del dataset.
- `02_lenet_vgg.ipynb`: entrenamiento y comparación de modelos CNN base.
- `03_transfer_learning.ipynb`: entrenamiento con Transfer Learning usando ResNet18.

### `src/`

Contiene código reutilizable del proyecto.

- `models.py`: definición de arquitecturas.
- `train.py`: funciones de entrenamiento y evaluación.
- `utils.py`: utilidades para carga de datos, métricas y soporte general.

### `results/`

Contiene resultados generados durante los experimentos.

- `figures/`: gráficas y visualizaciones.
- `metrics/`: métricas exportadas.
- `checkpoints/`: carpeta reservada para pesos de modelos entrenados.

Los checkpoints pesados no se suben al repositorio. Solo se conserva `.gitkeep` para mantener la carpeta visible.

## Instalación

Clonar el repositorio:

```bash
git clone https://github.com/Axel-Pariona/Blood-Cell-Deep-Learning-Comparison.git
cd Blood-Cell-Deep-Learning-Comparison
```

Crear un entorno virtual:

```bash
python -m venv .venv
```

Activar el entorno virtual en Windows PowerShell:

```powershell
.venv\Scripts\activate
```

Activar el entorno virtual en Linux o WSL:

```bash
source .venv/bin/activate
```

Instalar dependencias:

```bash
pip install -r requirements.txt
```

## Descarga del dataset

El dataset se descarga con los scripts ubicados en `data/`.

En Windows PowerShell:

```powershell
cd data
.\download_data.ps1
```

En Linux, macOS o WSL:

```bash
cd data
bash download_data.sh
```

Para usar la Kaggle API, se requiere configurar previamente el archivo `kaggle.json`.

Más información en:

[`data/README.md`](data/README.md)

## Ejecución de notebooks

Se recomienda ejecutar los notebooks en este orden:

```txt
1. notebooks/01_eda.ipynb
2. notebooks/02_lenet_vgg.ipynb
3. notebooks/03_transfer_learning.ipynb
```

También se incluye una versión reproducible para Colab:

```txt
notebooks/00_colab_reproducible.ipynb
```

## Flujo general del proyecto

```txt
Descarga del dataset
  ↓
Análisis exploratorio
  ↓
Preprocesamiento y carga de imágenes
  ↓
Entrenamiento de CNN base
  ↓
Evaluación con y sin Batch Normalization
  ↓
Análisis de learning rate
  ↓
Transfer Learning con ResNet18
  ↓
Comparación de métricas
  ↓
Visualización de resultados
```

## Modelos evaluados

El proyecto compara diferentes enfoques:

### CNN tipo LeNet

Modelo convolucional base utilizado como punto de partida para evaluar el desempeño inicial.

### CNN tipo VGG simplificada

Arquitectura más profunda inspirada en VGG, utilizada para analizar mejoras en extracción de características.

### Modelos con Batch Normalization

Variantes que incorporan Batch Normalization para mejorar estabilidad del entrenamiento y convergencia.

### Transfer Learning con ResNet18

Modelo preentrenado utilizado como extractor de características para mejorar el rendimiento con menor costo de entrenamiento.

## Resultados

Los resultados se almacenan en:

```txt
results/
  figures/
  metrics/
```

Las figuras pueden incluir:

- Curvas de entrenamiento.
- Curvas de validación.
- Comparaciones entre modelos.
- Matrices de confusión.
- Visualizaciones del dataset.

Las métricas pueden incluir:

- Accuracy.
- Precision.
- Recall.
- F1-score.
- Tiempo de entrenamiento.
- Comparación entre configuraciones.

## Reproducibilidad

Para reproducir el proyecto:

1. Instalar dependencias.
2. Configurar Kaggle API.
3. Descargar el dataset.
4. Ejecutar los notebooks en orden.
5. Revisar los resultados en `results/`.

La carpeta `results/checkpoints/` está preparada para almacenar pesos de modelos, pero los archivos grandes están excluidos del repositorio mediante `.gitignore`.

## Alcance del proyecto

Este proyecto tiene fines académicos y experimentales.

Incluye:

- Comparación de modelos CNN.
- Uso de Batch Normalization.
- Análisis de learning rate.
- Transfer Learning.
- Evaluación con métricas de clasificación.
- Documentación de resultados.

## Limitaciones

- El rendimiento depende de la calidad y balance del dataset.
- Los resultados pueden variar según hardware, semillas y configuración del entorno.
- El dataset debe descargarse externamente.
- Los checkpoints de modelos no se versionan en GitHub.
- El proyecto no está orientado a diagnóstico médico ni uso clínico.
- Las conclusiones corresponden a un contexto académico y experimental.

## Posibles mejoras

- Agregar control explícito de semillas para mayor reproducibilidad.
- Exportar todos los resultados a CSV o JSON.
- Incorporar más arquitecturas preentrenadas.
- Realizar búsqueda de hiperparámetros.
- Agregar validación cruzada.
- Implementar Grad-CAM para interpretabilidad.
- Crear un dashboard de resultados.
- Automatizar entrenamiento desde scripts CLI.
- Publicar un notebook resumen con las conclusiones finales.

## Estado del proyecto

Proyecto académico completo y reorganizado para presentación en GitHub.

## Autores

- Omar Junior Acuña Villegas
- Rafael Tomás Chui Sánchez
- Sebastián Meza
- Axel Yamir Pariona Rojas
