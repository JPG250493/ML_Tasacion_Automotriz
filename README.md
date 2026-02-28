# Modelado de Tasación Automotriz: Mercado Alemán (AutoScout24)

Este proyecto desarrolla un sistema de inteligencia artificial capaz de tasar vehículos de ocasión con alta precisión en el mercado alemán.

## 📋 Descripción del problema

El objetivo es resolver la falta de estandarización y el error humano en la valoración de vehículos de segunda mano. Se busca proporcionar a plataformas de compraventa y profesionales del sector una herramienta automática que prediga el precio de mercado de forma rápida y fundamentada, minimizando el riesgo financiero en cada operación.

## 📊 Dataset utilizado

* 
**Origen:** El dataset contiene datos públicos extraídos de **AutoScout24 Germany**.


* 
**Descripción:** Incluye más de 46,000 registros con variables críticas como caballos de fuerza (CV), kilometraje, marca, modelo, tipo de combustible y año de matriculación.


* 
**Acceso:** El conjunto de datos procesado se carga mediante archivos `.pk` o `.joblib` desde el directorio de datos del proyecto.



## 💡 Solución adoptada

Se ha seguido un enfoque de **aprendizaje supervisado (regresión)** comparando diversos algoritmos:

1. 
**Baseline:** Regresión Lineal para establecer el punto de partida técnico.


2. 
**Benchmarking:** Se evaluaron modelos de Árboles de Decisión, Random Forest, KNN y Gradient Boosting .


3. 
**Optimización:** Tras un proceso de ingeniería de variables (creación de `gama_marca` y `antigüedad`) y ajuste de hiperparámetros mediante `RandomizedSearchCV`, se seleccionó **Gradient Boosting** como modelo final.


* 
**Criterio de selección:** Se priorizó el **MAE (Error Medio Absoluto)** más bajo para garantizar la máxima precisión monetaria en cada tasación individual.




## 📁 Estructura del repositorio

```text
├── src/                # El directorio source que contiene el resto de carpetas
│   ├── data_sample/    # Archivos de datos de muestra (máx. 5MB) que permitan ejecutar el código
│   │   ├──processed/   #Archivos procesados tras el EDA
│   │   ├──raw/             #Archivos datasets originales para poder iniciar el EDA
│   ├── img/            # Imágenes utilizadas en el proyecto
│   ├── models/         # Modelos guardados en formato pickle o joblib
│   ├── notebooks/      # Notebooks de desarrollo y pruebas
│   ├── utils/          # Módulos, funciones auxiliares o clases creadas para el proyecto
├── main.ipynb          # Notebook final: claro, conciso y bien estructurado
├── Presentacion.pdf    # Documento soporte de la exposición en vídeo
├── README.md           # Fichero README resumen del proyecto

```

## 🛠️ Tecnologías utilizadas

* 
**Lenguaje:** Python 3.13.8 


* **Librerías principales:**
* 
`Pandas` y `NumPy`: Manipulación y limpieza de datos.


* 
`Scikit-learn`: Entrenamiento, evaluación y optimización de modelos de ML .


* 
`Joblib`: Persistencia de modelos y carga de datos.


* 
`Matplotlib` y `Seaborn`: Visualización de datos y análisis de importancia de variables.





## 🚀 Instrucciones de reproducción

1. Clona este repositorio.
2. Instala las dependencias: `pip install -r requirements.txt`.
3. Ejecuta el notebook principal `main.ipynb` ubicado en la carpeta `notebooks/`.


4. El modelo final se generará y guardará automáticamente en `src/models/`.



## 📈 Principales resultados

El modelo final optimizado ha demostrado un rendimiento excepcional comparado con el punto de partida:

* 
**Baseline (Regresión Lineal):** MAE de **4.541,99 €** [$R^2 = 0.7670$].


* 
**Modelo Final (Gradient Boosting):** MAE de **1.773,92 €** [$R^2 = 0.8919$].


* 
**Mejora:** Reducción del error de tasación en un **60.9%** respecto al baseline.



**Conclusión clave:** La potencia (CV) y la categoría de la marca (`gama_marca`) son los predictores más potentes del precio en el mercado alemán. El modelo es altamente fiable para vehículos de hasta 100.000 €, presentando ligeras desviaciones en el segmento de hiper-lujo debido a la exclusividad de dichos activos.
