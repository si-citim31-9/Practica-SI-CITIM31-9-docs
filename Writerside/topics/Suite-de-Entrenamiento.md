# Suite de Entrenamiento 

Para este proyecto, se ha desarrollado una serie de herramientas que cumplen las siguientes funciones:
- Extracción de descriptores (Características) en forma numérica de datasets de imágenes
- Creación de archivos ARFF (compatibles con WEKA) a partir de los descriptores de forma flexible
- Entrenamiento de un modelo a partir de los archivos ARFF, con distintos parámetros
- Evaluación de la eficiencia de los modelos obtenidos para poder obtener el mejor resultado para su posterior uso en el OCR

En la siguiente sección se encuentra una lista de los paquetes y las herramientas contenidas en ellos.

# Paquetes
### [Descriptores](Extracción-de-Descriptores.md)

Este paquete contiene las herramientas necesarias para extraer los descriptores de las imágenes y estos se dividen en varios módulos:

- extraccion.py 
- formas.py
- histogramasgo.py

### [Entrenamiento](Entrenamiento.md)

Este paquete contiene las herramientas necesarias para el entrenamiento de un modelo 
## Command

Syntax:

```shell
cmd [OPTIONS]
```

## Options

Describe what each option is used for:

-o, --open
: Opens a file.

-c, --close
: Closes a file.

-v, --version
: Displays version information.

-h, --help
: Displays help.

<seealso>
    <!--Provide links to related how-to guides, overviews, and tutorials.-->
</seealso>