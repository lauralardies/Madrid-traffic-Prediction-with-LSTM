# Predicción del tráfico de Madrid con LSTM

La dirección de GitHub para este repositorio es la siguiente: [Repositorio](https://github.com/lauralardies/Madrid-traffic-Prediction-with-LSTM).

## Índice

- [🔰 Introducción](#-introducción)
- [🧮 Datos](#-datos)
- [🗃️ Archivos](#-archivos)
- [🚀 Ejecución](#-ejecución)

## 🔰 Introducción

En este proyecto se trata de predecir el tráfico de Madrid, modelando una red neuronal LSTM, arquitectura capaz de captar patrones temporales a partir de secuencias de datos. Se hace esto con el objetivo de reducir las congestiones, reduciendo también por lo tanto las emisiones y mejorando la calidad de vida de los ciudadanos. A partir del modelo entrenado, se realizan predicciones, las cuales facilitarán la generación una red de carreteras con intensidades (valores predichos) asignadas a los nodos. Y ya por último, se calcula el camino mínimo mediante el algoritmo de Dijkstra, mundialmente conocido y con un costo computacional bajo, además de estimar el tiempo del trayecto basándose en la distancia recorrida (se calcula la distancia euclidea entre dos puntos) y la velocidad media (valor que también predice el modelo). 

En el repositorio actual se pueden encontrar varios cuadernos de Jupyter con Python y Markdown que, celda por celda, van desarrollando todo el proceso descrito.

## 🧮 Datos

Para entrenar un modelo para que prediga el tráfico, se necesita acceso a los siguientes datos:

- Un historial de datos de tráfico de Madrid, a partir de los cuales el modelo aprenderá e identificará patrones para predecir el tráfico correctamente.
- Datos en tiempo real que se emplean para realizar simulaciones de hora de llegada estimada y recomendaciones de horas de salida a partir de una hora de llegada dada.

> ¿De dónde se obtienen los datos? Para este estudio, se recopilaron datos desde el [portal de datos abiertos del Ayuntamiento de Madrid](https://datos.madrid.es/portal/site/egob), más concretamente, el [histórico de datos de tráfico desde 2013](https://datos.madrid.es/sites/v/index.jsp?vgnextoid=33cb30c367e78410VgnVCM1000000b205a0aRCRD&vgnextchannel=374512b9ace9f310VgnVCM100000171f5a0aRCRD) y los [datos del tráfico en tiempo real](https://datos.madrid.es/sites/v/index.jsp?vgnextoid=02f2c23866b93410VgnVCM1000000b205a0aRCRD&vgnextchannel=374512b9ace9f310VgnVCM100000171f5a0aRCRD), pero no han sido adjuntados en este repositorio debido a su gran volumen.

## 🗃️ Archivos

El repositorio está organizado de la siguiente manera:

- Una carpeta general, desde la cual se puede acceder a el códio completo laldama `Traffic`.
- Una carpeta llamada `models` donde se encuentran las cuatro distintas variaciones de modelos desarrollados a lo largo del estudio: `lstm.ipynb` para la red más básica, `lstm2.ipynb` para una red algo más compleja, `lstm2_cyclical.ipynb` para la misma red anterior pero aplicando transformaciones sobre las variables cíclicas y `lstm_attention.ipynb` algo más sencilla que la anterior (aplicando también la transformación sobre las variables cíclicas) e integrando en la red una capa de atención.
- Una carpeta llamada `optimization` desde la cual se hacen todas las simulaciones de cálculo de camino mínimo y estimación de tiempo de trayecto. Se pueden encontrar dos archivos: `graph.ipynb` que se encarga de generar el grafo y actualizar sus intensidades según los valores predichos, y `dijkstra.ipynb` que, a partir del grafo con intensidades, calcula el camino mínimo y estima la hora de salida o llegada, según el caso.
- Una carpeta llamada `predictions` que contiene tan solo un documento, `prediction.ipynb` que se encarga de cargar un modelo entrenado, hacer las predicciones correspondientes y guardarlas para su uso a posteriori.
- Una carpeta llamada `process data`, encargada de todo lo que tiene que ver sobre el análisis de datos previo a todo el entrenamiento de modelos y predicciones. Se pueden unir los datos mensuales en un único CSV (`unite_data.ipynb`), visualizar los datos en un mapa (`map_data.ipynb`), generar gráficas de los datos (`visualization.ipynb`) y separar los datos en dsitintos CSVs según su identificador (`separate_data.ipynb`).

Todos estos archivos y documentos constituyen el código generado para mi trabajo de fin de grado.

## 🚀 Ejecución

Para que se ejecuten todos los archivos de código correctamente, se debe seguir el siguiente flujo de proceso:

1. Descargar los datos del portal de datos abiertos del Ayuntamiento de Madrid y almacenarlos en una nueva carpeta llamada `data`, dentro de `Traffic`. Además, guardar los datos históricos mensuales en otra carpeta dentro de `data` llamada `monthly data`.
2. Ejecutar el archivo `unite_data.ipynb` para unir en un único CSV las entradas mensuales de datos.
3. En caso de querer visualizar los datos, ejecutar `map_data.ipynb` y `visualization.ipynb`.
4. Para preparar los datos para entrenar modelos, ejecutar `separate_data.ipynb`, de esta manera se separan los datos según identificadores.
5. Ejecutar cualquiera de los modelos que se deseen dentro de la carpeta `models`, pudiendo cambiar el conunto de datos de entrenamiento libremente para cada caso. El modelo y escalador se guardan automáticamente en una carpeta llamada `saved`.
6. Antes de ejecutar el código de `prediction.ipynb`, ejecutar un modelo para cada set de datos separados en el paso 4 y guardarlo en una carpeta llamada `final` dentro de `models`.
7. Cuando ya se tiene un modelo por cada punto seleccionado, se pueden realizar las predicciones de `prediction.ipynb`, obteniendo 3 archivos tipo `pkl`.
8. Una vez hechas las predicciones, se puede generar el grafo y asignarle intensidades, ejecutando el archivo `graph.ipynb` dentro de la carpeta `optimization`.
9. Con el grafo generado y con ponderaciones, se puede calcular el camino mínimo ejecutando `dijkstra.ipynb`, donde tambén se obtiene la estimación de la duración del trayecto.
