# Predicción del tráfico de Madrid con LSTM

La dirección de GitHub para este repositorio es la siguiente: [GitHub](https://github.com/lauralardies/Madrid-traffic-Prediction-with-LSTM)
https://github.com/lauralardies/Madrid-traffic-Prediction-with-LSTM

## Índice

- [🔰 Introducción](#introducción)
- [🧮 Datos](#datos)
- [🗃️ Archivos](#archivos)
- [🚀 Ejecución](#ejecución)

## 🔰 Introducción

En este proyecto se trata de predecir el tráfico de Madrid, modelando una red neuronal LSTM, arquitectura capaz de captar patrones temporales a partir de secuencias de datos. Se hace esto con el objetivo de reducir las congestiones, reduciendo también por lo tanto las emisiones y mejorando la calidad de vida de los ciudadanos. A partir del modelo entrenado, se realizan predicciones, las cuales facilitarán la generación una red de carreteras con intensidades (valores predichos) asignadas a los nodos. Y ya por último, se calcula el camino mínimo mediante el algoritmo de Dijkstra, mundialmente conocido y con un costo computacional bajo, además de estimar el tiempo del trayecto basándose en la distancia recorrida (se calcula la distancia euclidea entre dos puntos) y la velocidad media (valor que también predice el modelo). En el repositorio actual se pueden encontrar varios cuadernos de Jupyter con Python y Markdown que, celda por celda, van desarrollando todo el proceso descrito.

## 🧮 Datos

Para entrenar un modelo para que prediga el tráfico, se necesita acceso a los siguientes datos:
- Un historial de datos de tráfico de Madrid, a partir de los cuales el modelo aprenderá e identificará patrones para predecir el tráfico correctamente.
- Datos en tiempo real que se emplean para realizar simulaciones de hora de llegada estimada y recomendaciones de horas de salida a partir de una hora de llegada dada.

> ¿De dónde se obtienen los datos? Para este estudio, se recopilaron datos desde el [portal de datos abiertos del Ayuntamiento de Madrid](https://datos.madrid.es/portal/site/egob), más concretamente, el [histórico de datos de tráfico desde 2013](https://datos.madrid.es/sites/v/index.jsp?vgnextoid=33cb30c367e78410VgnVCM1000000b205a0aRCRD&vgnextchannel=374512b9ace9f310VgnVCM100000171f5a0aRCRD) y los [datos del tráfico en tiempo real](https://datos.madrid.es/sites/v/index.jsp?vgnextoid=02f2c23866b93410VgnVCM1000000b205a0aRCRD&vgnextchannel=374512b9ace9f310VgnVCM100000171f5a0aRCRD), pero no han sido adjuntados en este repositorio debido a su gran volumen.

## 🗃️ Archivos

El repositorio está organizado de la siguiente manera.


## 🚀 Ejecución

Para que se ejecuten todos los archivos de código correctamente, se debe seguir el siguiente flujo de proceso:
1º
2º
...
