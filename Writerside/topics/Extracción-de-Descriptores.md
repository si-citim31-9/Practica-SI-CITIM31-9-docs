# Descriptores

El paquete descriptores contiene un módulo principal de procesamiento (extraccion.py) y dos módulos adicionales que se utilizan desde el anteriormente mencionado.

## extraccion.py

### Funciones de extracción:
<br/>


```
obtener_imagenes(path_recursos)
```
Función que dado un el ```path``` de un dataset, recorre sus carpetas y devuelve un ```dict``` con forma ```(imagen, etiqueta)```


path_recursos
: ```String``` : Ruta al archivo a procesar

> [Importante]
> El formato de los dataset debe ser: ```<num>/<num>_<indice>.png```
> Siendo los números (0-35) es decir (0-9 y a-z) y el índice representando el número de archivo en la carpeta.

<br/>
```
extraccion_batch(imagenes, opciones, debug_level)
```
Función que extrae de un ```dict``` con la estructura ```(imagen,etiqueta)``` los descriptores indicados en una lista con varias opciones.
Devuelve una lista de listas en las que, por cada descriptor/grupo de descriptores extraídos, incluye ```tipo de extracción```,```opciones``` y ```path del fichero generado```.

images
: ```dict (imagen,etiqueta)``` Debe contener la imagen extraída con OpenCV.IMREAD y su correspondiente etiqueta.

opciones
: ```list[(tipo,opciones)]``` Debe contener, por cada tipo de extracción a realizar, su tipo en forma de ```string``` y sus opciones con forma ```list```.

debug_level
: ```int```: cantidad de notificaciones que deben mostrarse en pantalla sobre el progreso. Por defecto es 0.

```
extraccion(images, opciones, fichero_destino, debug_level, **kwargs)
```
Función que extrae de un ```dict``` con la estructura ```(imagen,etiqueta)``` el descriptor indicado en el resto de los parámetros, devolviendo un archivo ```ARFF```

images
: ```dict (imagen,etiqueta)``` Debe contener la imagen extraída con OpenCV.IMREAD y su correspondiente etiqueta. 

opciones
: ```String``` que contiene "histogramas" o "formas" según el tipo que de extracción que se quiera realizar

fichero_destino
: ```String``` que contiene el ```path``` en el que la función tendrá que crear el archivo ARFF

debug_level
: ```int```: cantidad de notificaciones que deben mostrarse en pantalla sobre el progreso. Por defecto es 0.

**kwargs
: ```list``` con contenido que depende de la opción elegida en el parámetro ```opciones```.
- "Histogramas": los kwargs deberán contener una ```list``` llamada ```histoptions``` con los parámetros:
    - ```Orientaciones```: int
    - ```Píxeles por celda```: int
    - ```Celdas por bloque```: int
    - ```feature_vector```: Boolean
- "Formas": los kwargs deberán contener una ```list``` llamada "formas" en las que se incluyen las funciones para extraer los descriptores de formas:
    - ```descriptores.formas.hu_moments``` 
    - ```descriptores.formas.aspect_ratio``` 
    - ```descriptores.formas.euler_moment``` 
    - ```descriptores.formas.compactness``` 

```
extraccion_ocr(imagenes, opciones, fichero_destino,debug_level)
```
Función que a partir de una ```list``` de imágenes y una ```list```con opciones extrar un fichero ```ARFF``` con la columna "label" = "?".
Su principal uso es extraer las propiedades de una imagen con la cual se quiere realizar una predicción.

images
: ```list``` Debe contener la imagen extraída con OpenCV.IMREAD.

opciones
: ```String``` que contiene "histogramas" o "formas" según el tipo que de extracción que se quiera realizar

fichero_destino
: ```String``` que contiene el ```path``` en el que la función tendrá que crear el archivo ARFF

debug_level
: ```int```: cantidad de notificaciones que deben mostrarse en pantalla sobre el progreso. Por defecto es 0.

**kwargs
: ```list``` con contenido que depende de la opción elegida en el parámetro ```opciones```.
- "Histogramas": los kwargs deberán contener una ```list``` llamada ```histoptions``` con los parámetros:
  - ```Orientaciones```: int
  - ```Píxeles por celda```: int
  - ```Celdas por bloque```: int
  - ```feature_vector```: Boolean
- "Formas": los kwargs deberán contener una ```list``` llamada "formas" en las que se incluyen las funciones para extraer los descriptores de formas:
  - ```descriptores.formas.hu_moments```
  - ```descriptores.formas.aspect_ratio```
  - ```descriptores.formas.euler_moment```
  - ```descriptores.formas.compactness```

## formas.py

### Funciones de formas:

```
aspect_ratio(image)
```
Función que devuelve el ratio de aspecto en forma ```double``` de una imagen. 

image
: ```np.array```: que contiene la imagen extraída por OpenCV

<br/>
```
compactness(image)
```
Función que devuelve la compacidad en forma ```float``` de una imagen. [docs](https://docs.opencv.org/2.4/modules/imgproc/doc/structural_analysis_and_shape_descriptors.html?highlight=moments#structural-analysis-and-shape-descriptors)

image
: ```np.array```: que contiene la imagen extraída por OpenCV



<br/>
```
hu_moments(image)
```
Función que devuelve los momentos invariables de Hu en forma ```list (float)``` de una imagen. [docs](https://docs.opencv.org/3.4/d0/d49/tutorial_moments.html)

image
: ```np.array```: contiene la imagen extraída por OpenCV

<br/>
```
euler_number(image)
```
Función que devuelve el número de Euler en forma ```float``` de una imagen. [docs](https://docs.opencv.org/4.x/d1/d32/tutorial_py_contour_properties.html)

image
: ```np.array```: contiene la imagen extraída por OpenCV

## histogramasgo.py

### Funciones de Histogramas:

```
extraer_histogramas(imagen,orientaciones, pixelspercell,cellsperblock,tamano)
```
Función que extrae los histogramas de una imagen en forma de ```list```.

imagen
: ```np.array```: contiene la imagen extraída por OpenCV

orientaciones
: ```int```: número de orientaciones de las que extraer los histogramas

pixelspercell
: ```int```: número de píxeles por celda


cellsperblock
: ```int```: número de celdas por bloque

tamano
: ```(int,int)```: área sobre la que operar para extraer los histogramas
