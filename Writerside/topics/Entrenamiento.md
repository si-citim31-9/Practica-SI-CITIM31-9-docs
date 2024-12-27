# Entrenamiento

Este paquete contiene dos módulos:
- ```main.py```: Contiene el código el flujo de entrenamiento de los modelos
- ```ocr.py```: Contiene la herramienta para el reconocimiento de carácteres

## main.py

### Funciones 

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