# Methodology

Este documento describe la metodología aplicada en el proyecto **Blood Cell Deep Learning Comparison**.

El proyecto se enfoca en comparar diferentes enfoques de Deep Learning para clasificación de imágenes de células sanguíneas.

## 1. Planteamiento del problema

El problema consiste en clasificar imágenes de células sanguíneas en cuatro clases principales:

```txt
EOSINOPHIL
LYMPHOCYTE
MONOCYTE
NEUTROPHIL
```

Esta tarea se aborda como un problema de clasificación multiclase mediante redes neuronales convolucionales y Transfer Learning.

## 2. Obtención del dataset

El dataset se obtiene desde Kaggle mediante scripts incluidos en la carpeta `data/`.

El flujo de descarga es:

```txt
Kaggle API
  ↓
Script de descarga
  ↓
Descompresión del dataset
  ↓
Carpetas TRAIN y TEST
```

El dataset no se versiona en GitHub por su tamaño.

## 3. Análisis exploratorio de datos

El análisis exploratorio se realiza en:

```txt
notebooks/01_eda.ipynb
```

Durante esta etapa se revisan aspectos como:

- Estructura de carpetas.
- Cantidad de imágenes por clase.
- Distribución de clases.
- Ejemplos visuales de imágenes.
- Dimensiones y características generales del dataset.

El objetivo del EDA es verificar que los datos estén correctamente organizados antes del entrenamiento.

## 4. Preprocesamiento

Las imágenes se preparan para ser utilizadas por modelos de Deep Learning.

El preprocesamiento puede incluir:

- Redimensionamiento.
- Conversión a tensores.
- Normalización.
- Separación entre entrenamiento, validación y prueba.
- Aplicación de transformaciones de datos.

En PyTorch, este flujo se implementa usando transformaciones de `torchvision.transforms`.

## 5. Carga de datos

La carga de datos se realiza mediante utilidades de PyTorch, como:

```txt
ImageFolder
DataLoader
```

`ImageFolder` permite leer imágenes organizadas en carpetas por clase.

`DataLoader` permite procesar los datos en lotes durante el entrenamiento y la evaluación.

## 6. Modelos CNN base

La primera etapa experimental compara modelos convolucionales base.

Estos modelos permiten establecer una línea base de rendimiento antes de aplicar técnicas más avanzadas.

### Modelo tipo LeNet

Arquitectura convolucional simple utilizada como baseline.

Características generales:

- Pocas capas convolucionales.
- Capas de pooling.
- Capas completamente conectadas.
- Menor costo computacional.

### Modelo tipo VGG simplificado

Arquitectura más profunda inspirada en VGG.

Características generales:

- Bloques convolucionales más profundos.
- Mayor capacidad de extracción de características.
- Mayor costo computacional que LeNet.

## 7. Batch Normalization

Se evalúa el impacto de Batch Normalization sobre el entrenamiento.

Batch Normalization ayuda a estabilizar la distribución de activaciones internas, lo que puede mejorar:

- Estabilidad del entrenamiento.
- Velocidad de convergencia.
- Rendimiento de validación.
- Robustez ante cambios de learning rate.

El proyecto compara modelos con y sin Batch Normalization para observar su efecto experimental.

## 8. Análisis del learning rate

Se prueban diferentes configuraciones de tasa de aprendizaje para analizar su impacto en el entrenamiento.

Un learning rate muy alto puede generar inestabilidad.

Un learning rate muy bajo puede hacer que el entrenamiento avance lentamente.

El objetivo es observar cómo este hiperparámetro afecta la pérdida, precisión y convergencia de los modelos.

## 9. Transfer Learning

La etapa final aplica Transfer Learning usando ResNet18.

El Transfer Learning permite aprovechar un modelo previamente entrenado en un dataset grande y adaptarlo a una nueva tarea.

Flujo general:

```txt
ResNet18 preentrenado
  ↓
Reemplazo de capa final
  ↓
Entrenamiento sobre dataset de células sanguíneas
  ↓
Evaluación del modelo
```

Este enfoque suele mejorar el rendimiento cuando el dataset disponible es limitado o cuando se requiere una extracción de características más robusta.

## 10. Entrenamiento

El entrenamiento de los modelos sigue un flujo general:

```txt
Modelo
  ↓
Función de pérdida
  ↓
Optimizador
  ↓
Forward pass
  ↓
Cálculo de pérdida
  ↓
Backpropagation
  ↓
Actualización de pesos
  ↓
Evaluación
```

Durante el entrenamiento se registran métricas como:

- Loss de entrenamiento.
- Loss de validación.
- Accuracy de entrenamiento.
- Accuracy de validación.

## 11. Evaluación

La evaluación permite comparar los modelos entrenados.

Métricas consideradas:

- Accuracy.
- Precision.
- Recall.
- F1-score.
- Matriz de confusión.
- Tiempo de entrenamiento.

Los resultados se guardan en:

```txt
results/metrics/
results/figures/
```

## 12. Comparación de modelos

La comparación final considera:

- Rendimiento predictivo.
- Estabilidad del entrenamiento.
- Complejidad del modelo.
- Impacto de Batch Normalization.
- Impacto del learning rate.
- Ventajas del Transfer Learning.

Esta comparación permite identificar qué enfoque ofrece mejor balance entre precisión y costo computacional para el dataset utilizado.

## 13. Organización de resultados

Los resultados se almacenan en dos carpetas principales:

```txt
results/figures/
results/metrics/
```

### `results/figures/`

Contiene gráficos, visualizaciones y matrices de confusión.

### `results/metrics/`

Contiene archivos con métricas generadas durante los experimentos.

La carpeta `results/checkpoints/` se reserva para pesos de modelos, pero los archivos pesados no se suben al repositorio.

## 14. Reproducibilidad

Para reproducir los experimentos se recomienda:

1. Crear un entorno virtual.
2. Instalar dependencias.
3. Configurar Kaggle API.
4. Descargar el dataset.
5. Ejecutar los notebooks en orden.
6. Revisar resultados en `results/`.

El notebook `00_colab_reproducible.ipynb` permite ejecutar una versión preparada para Google Colab.

## 15. Limitaciones

El proyecto tiene algunas limitaciones:

- Los resultados pueden variar por hardware y configuración.
- El dataset debe descargarse externamente.
- Los checkpoints no se incluyen por tamaño.
- No se orienta a diagnóstico médico.
- El análisis tiene fines académicos y experimentales.
- El rendimiento puede depender de la distribución del dataset.

## 16. Posibles mejoras

Se podrían implementar mejoras como:

- Control de semillas en todos los experimentos.
- Búsqueda sistemática de hiperparámetros.
- Pruebas con más arquitecturas preentrenadas.
- Grad-CAM para interpretabilidad.
- Validación cruzada.
- Exportación automática de métricas.
- Comparación con modelos más ligeros.
- Automatización mediante scripts CLI.

## Conclusión

La metodología aplicada permite comparar modelos CNN base, variantes con Batch Normalization y Transfer Learning con ResNet18. El proyecto evidencia cómo diferentes técnicas de Deep Learning influyen en el rendimiento de clasificación de imágenes y sirve como práctica académica de visión por computadora.
