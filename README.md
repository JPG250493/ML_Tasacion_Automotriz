# AutoValue Pro: Optimización de Estrategia de Precios para el Mercado de Ocasión mediante Regresión Avanzada.

1. Elección de temática y obtención de datos

### Enfoque

    Se ha seleccionado un dataset robusto para resolver un desafío crítico en el sector Automotive Retail.

### Problemática de "negocio"

    El mercado de coches de segunda mano es altamente volátil. Un concesionario digital (estilo AutoScout24 o Clicars) se enfrenta al reto de tasar vehículos de forma competitiva y rápida. Si el precio es muy alto, el coche se queda "cogiendo polvo" en el inventario; si es muy bajo, se pierde margen de beneficio. El objetivo es crear un modelo de tasación automática que minimice el error humano y maximice el ROI (Retorno de Inversión) al adquirir y vender stock.

### Datasets seleccionados

    - autoscout24-germany-dataset. Contiene datos reales de ofertas de vehículos en el mercado alemán (referente europeo), con variables técnicas críticas como potencia (hp), kilometraje (mileage), marca, modelo y tipo de cambio.


2. Validación de datos y planteamiento del problema

El dataset cuenta con miles de registros (más de 46.000 en las versiones estándar de este CSV), lo que garantiza volumen suficiente para el entrenamiento. El formato es un CSV limpio y estructurado, listo para el procesamiento con Pandas.

Disponemos de 9 variables de entrada de alto impacto.

Numéricas: mileage, hp, year.

Categóricas: make, model, fuel, gear, offertype.

El precio de un coche no se deprecia de forma lineal. La interacción entre la marca (prestigio), el tipo de combustible (etiquetas medioambientales) y el kilometraje crea un escenario de correlaciones no lineales que el Machine Learning puede capturar mucho mejor que una simple tabla de Excel o una media aritmética.

Variable Objetivo (Target): price. Se trata de un problema de Aprendizaje Supervisado - Regresión, ya que buscamos predecir un valor numérico continuo (Euros).


Métrica de Éxito: Se propone el MAE (Mean Absolute Error) para que el negocio entienda fácilmente la desviación media en euros de cada tasación.