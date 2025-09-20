# Análisis Predictivo de Videojuegos: Explorando el Éxito de la Nintendo Switch
Autor: Macchi, Leandro Nicolás
Profesor: Araque, Leandro
Curso: Data Science 2, CODERHOUSE
Comisión: 75700

# Introducción
Este trabajo práctico hace hincapié en el análisis de la industria de los videojuegos, centrándose en la exitosa consola Nintendo Switch. El trabajo se estructura en dos fases principales. La primera, de análisis exploratorio, permite comprender las dinámicas del mercado, como la explosión de lanzamientos a partir de 2017 y la fuerte correlación entre la popularidad de un juego y su calificación. La segunda fase, de modelado predictivo, busca capitalizar estos insights para construir modelos de machine learning que predigan el éxito de los títulos.

El objetivo es doble: por un lado, predecir la calificación de un juego, y por otro, clasificar si un juego se convertirá en un éxito comercial. Para ello, se aplicarán técnicas avanzadas de Feature Selection y Feature Engineering para optimizar el dataset, y se evaluará el rendimiento de múltiples algoritmos de regresión y clasificación.

# Metodología y Análisis Exploratorio de Datos (EDA)
El proyecto se inicia con la recopilación de datos a través de una API, garantizando la calidad y la estructura de la información. La base de datos, con 3000 registros, incluye métricas de compromiso de usuarios, calificaciones y popularidad.

Durante el EDA, se validaron varias hipótesis clave:

Análisis Unilateral: La distribución de las calificaciones y otras métricas numéricas mostró una clara distribución de cola larga, indicando que la mayoría de los juegos son nichos, mientras que unos pocos títulos son éxitos masivos (outliers).

Análisis Bilateral: Se confirmó una fuerte correlación positiva entre la cantidad de reseñas de un juego y su calificación, sugiriendo que el mercado premia la calidad.

Análisis Multilateral: Un mapa de calor de correlaciones reveló que las métricas de popularidad (reviews_count, ratings_count, count_owned) están intrínsecamente ligadas. Esto nos permitió crear un insight clave: el éxito comercial se traduce directamente en un mayor compromiso del jugador.

# Modelado y Predicción con Machine Learning
En esta etapa, se prepararon los datos para el modelado. Se aplicó Feature Engineering para crear nuevas variables como la tasa de finalización y la tasa de abandono de los juegos. Posteriormente, se utilizó Feature Selection (RFE y SelectKBest) para elegir las características más relevantes, reduciendo la dimensionalidad del dataset sin perder información crucial.

Modelos de Regresión (Predicción de Calificación)
Se evaluaron tres modelos: Regresión Lineal, Ridge y RandomForestRegressor.

Resultados Originales: El RandomForestRegressor demostró un rendimiento superior, con un coeficiente R2 de 0.8066, explicando la gran mayoría de la varianza en las calificaciones. La Regresión Lineal y Ridge mostraron un rendimiento muy limitado (R2 < 0.5).

Optimización de Hiperparámetros: El ajuste de hiperparámetros no mejoró significativamente el rendimiento de RandomForestRegressor, sugiriendo que su configuración inicial ya era óptima para los datos. Se comprobó que la elección del modelo base es más crítica que el ajuste fino para este problema.

Modelos de Clasificación (Predicción de Popularidad)
El objetivo fue clasificar si un juego sería popular. Se utilizó Regresión Logística y se evaluó con métricas y una matriz de confusión. Como un "bonus track", se implementó un modelo de ensemble, XGBoost, para intentar mejorar la tasa de detección.

Resultados: El modelo de Regresión Logística logró una alta exactitud (Accuracy: 0.9117) y precisión (Precision: 0.8929). Sin embargo, el Recall (0.7669) fue su punto débil, indicando que el modelo no lograba identificar a todos los juegos que eran realmente populares. Se utilizó la matriz de confusión para visualizar este problema, identificando un número significativo de Falsos Negativos.

# Conclusiones y Futuras Mejoras
Este proyecto demostró que el análisis de datos es una herramienta poderosa para entender y predecir el comportamiento en la industria de los videojuegos. Los modelos confirman que la popularidad y el compromiso son los principales impulsores de la calidad percibida de un juego.

Si bien los modelos de regresión y clasificación lograron un rendimiento sólido, hay oportunidades para seguir mejorando. Una futura iteración podría centrarse en:
Ajustar los hiperparámetros del modelo XGBoost de forma más exhaustiva para optimizar el recall.
Explorar otros modelos de clasificación avanzados como LightGBM.

Incorporar variables categóricas como género y modo de juego en los modelos de predicción.
