# [Re] Instance-aware-colorization
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/141ZkxJ3H8Ano97-MU1g4buTq-AMqVym0#scrollTo=NKNjpox0M_-y)

Para la reproducción del articulo [''Instance-aware-colorization''](https://ieeexplore.ieee.org/document/9157351), se utilizo Google Colab y se siguió los siguientes pasos:

## 01 - Entorno de Configuración

### Requerimientos:

- CUDA 10.1
- Python3 (preinstalado)
- Pytorch >= 1.5
- Detectron2
- OpenCV-Python (preinstalado)
- Pillow/scikit-image (preinstalado)

## 02 - Clonamos el repositorio oficial del código fuente del artículo

```bash
!git clone https://github.com/ericsujw/InstColorization
```
```bash
%cd InstColorization/
```

## 03 - Descargamos el modelo pre-entrenado

Para obtener los bounding box de las imágenes necesitamos el modelo pre-entrenado ''Mask R-CNN'' de detección de objetos propuesto por Zhang et al.

```bash
!sh scripts/download_model.sh
```

## 04 - Detectando los bounding box de objetos

Para este paso realizamos la configuración previa del Detectron2. Creamos una carpeta de bounding boxs para guardar los resultados de nuestra predicción. Esta carpeta estará con el nombre de ''example_bbox''. Luego, pasamos las imágenes de entrada de RGB a LAB. Tomamos el canal L como nuestra entrada y nos aseguramos de que podamos obtener resultados de predicción de los bounding box consistentes.

## 05 - Colorizando imágenes
- Configuramos las librerias correspondientes para la colorización de imágenes por instancia y a imágen completa. 
- Luego, creamos una carpeta de resultados para guardar nuestras imágenes de color predichas. 
-Después, cargamos el modelo de fusión previamente entrenado obtenido del repositorio oficial.
- Y finalmente empezamos con la colorización de imágenes.Para la colorización por instancia se requiere de los bounding box detectados previamente. 
- Una vez coloreado las imágenes por las dos redes (por instancia y a imagen competa), las enviamos al modelo de fusión cargado para obtener las imágenes ya colorizadas.

## 06 - Visualizando resultados

Para la visualización de los resultados se tomó de ejemplos algunas imágenes. En esta sección mostramos la imagen de entrada en escala de grises y la imágen de salida a color.
