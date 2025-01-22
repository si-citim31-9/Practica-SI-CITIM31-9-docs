# Herramientas

Este paquete contiene funciones varias.

##### traducir_predicciones
```
traducir_predicciones(predicciones)
```
A partir de una `list` de números del rango `0-35` obtiene sus equivalentes en el alfabeto de la práctica `(0-9 a-z)`

predicciones
: `list("String")` : Lista con el output de una predicción

##### contar_carpetas
```
contar_carpetas(ruta)
```
A partir de un `path` devuelve el número de carpetas/directorios que contiene

ruta
: `path`: Ruta absoluta a la carpeta/directorio

##### obtener_pngs
```
obtener_pngs(ruta)
```
A partir de un `path` obtiene las rutas a todos los archivos `.png` que existen en el directorio en forma de `list(String)`.

##### eliminar_archivos_no_usados
```
eliminar_archivos_no_usados(carpeta_datasets, carpeta_modelos, resultado)
```
Función que elimina todos los datasets y modelos menos los más óptimos obtenidos en la función `obtener_modelo`.

carpeta_datasets
: `path`: ruta relativa al directorio contenedor de los datasets

carpeta_modelos
: `path`: ruta relativa al directorio contenedor de los modelos

resultado
: `list`: output de la función de `obtener_modelo`

##### eliminar_archivos
```
eliminar_archivos(ruta_carpeta)
```
Función que elimina todos los archivos de una carpeta

ruta_carpeta
: `path`: ruta absoluta a la carpeta

##### procesar_imagen
```
procesar_imagen(imagen)
```
Función que aplica unos ajustes (convierte a binaria) para preparar una imagen para otras funciones.

imagen
: `path`: ruta absoluta a la imagen

##### mostrar_imagen
```
mostrar_imagen(imagen)
```
Función para mostrar una imagen (para pruebas)

imagen
: `np.array`: imagen ya abierta con `OpenCV.imread`

##### tqdm_conditional
```
tqdm_conditional(iterable,desc,debug_level)
```
Función que muestra una barra de progreso dependiendo de `debug_level`

iterable
: `iterable`: item sobre el que se realiza el bucle `for`

desc
: `String`: texto que se quiere mostrar antes de la barra de progreso

debug_level
: `int`: `0` para no mostrar la barra y `1` para mostrarla
