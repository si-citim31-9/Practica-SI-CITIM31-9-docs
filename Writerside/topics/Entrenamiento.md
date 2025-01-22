# Entrenamiento

Este paquete contiene dos módulos:
- ```main.py```: Contiene el código el flujo de entrenamiento de los modelos
- ```ocr.py```: Contiene la herramienta para el reconocimiento de carácteres

## main.py

##### training 

```
training(dataset, fichsalida, clasificador, debug_level)
```
Esta función realiza el entrenamiento de un modelo a partir del dataset propocionado. 
Devuelve un ```list``` con la forma ```[dataset,fichsalida,modelo]```

dataset
: ```path```: ruta a archivo ARFF con los datos extraídos del dataset inicial


fichsalida
: ```path```: ruta en la que se generará el archivo ```.model``` tras el entrenamiento

clasificador
: ```String ```: clasificador que se utilizará para el entrenamiento del modelo (por defecto weka.classifiers.trees.RandomForest)

debug_level
: ```int```: cantidad de notificaciones que deben mostrarse en pantalla sobre el progreso. Por defecto es 0.


##### obtener_modelo
```
obtener_modelo(opciones, classifiers, path_recursos, raiz_proyecto)
```

Función que entrena una selección de modelos a partir de un dataset, unas parámetros y unos clasificadores.
Tras completar el/los entrenamiento/s, crea una tabla con todos los entrenamientos, escoge el mejor según el porcentaje de aciertos y devuelve la ruta del fichero y sus parámetros.

opciones
: ```list[("formas"|"histogramas,[opciones_extracción])]```: Lista que contiene listas que contienen el tipo de extracción y sus parámetros.

classifiers
: ```list(String)```: Lista de clasificadores (usando el namescheme de WEKA) para utilizar en el entrenamiento del modelo.

path_recursos
: ```path```: ruta (relativa al proyecto) del directorio donde se encuentran los datasets en formato ```ARFF```.

raiz_proyecto
: ```path```: ruta absoluta (desde la raíz del sistema) a la carpeta raíz del proyecto

## ocr.py

##### predecir
```
predecir(modelo_path, arff_path)
```
Realiza una predicción sobre las instancias contenidas en un archivo ```ARFF``` a partir de un modelo

modelo_path
: ```path```: ruta absoluta al fichero ```.model```que se quiere utilizar para realizar la predicción

arff_path
: ```path```: ruta absoluta al fichero ```ARFF``` sobre el que se quiere realizar la predicción. La última columna ("label") debe ser "?" para todas las instancias.