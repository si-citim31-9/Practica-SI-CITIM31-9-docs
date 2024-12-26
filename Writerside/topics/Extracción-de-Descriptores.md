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
extraccion(images, opciones, fichero_destino, **kwargs)
```
Función que extrae de un ```dict``` con la estructura ```(imagen,etiqueta)``` los descriptores indicados en el resto de los parámetros, devolviendo un archivo ```ARFF```

images
: ```dict (imagen,etiqueta)``` Debe contener la imagen extraída con OpenCV.IMREAD y su correspondiente etiqueta. 

opciones
: ```String``` que contiene "histogramas" o "formas" según el tipo que de extracción que se quiera realizar

fichero_destino
: ```String``` que contiene el ```path``` en el que la función tendrá que crear el archivo ARFF

**kwargs
: ```list``` con contenido que depende de la opción elegida en el parámetro ```opciones```.
- "Histogramas": los kwargs deberán contener una ```list``` llamada ```histoptions``` con los parámetros:
    - ```Orientaciones```: int
    - ```Píxeles por celda```: (int,int)
    - ```Celdas por bloque```: (int,int)
    - ```feature_vector```: Boolean
- "Formas": los kwargs deberán contener una ```list``` llamada "formas" en las que se incluyen las funciones para extraer los descriptores de formas:
    - ```descriptores.formas.hu_moments``` 
    - ```descriptores.formas.aspect_ratio``` 
    - ```descriptores.formas.euler_moment``` [docs](https://sydney4.medium.com/the-euler-number-of-a-binary-image-1d3cc9e57caa)
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
: ```np.array```: que contiene la imagen extraída por OpenCV

<br/>
```
euler_number(image)
```
Función que devuelve el número de Euler en forma ```float``` de una imagen. [docs](https://docs.opencv.org/4.x/d1/d32/tutorial_py_contour_properties.html)

image
: ```np.array```: que contiene la imagen extraída por OpenCV
