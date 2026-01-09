# proyecto_sprint_14

## Etapa 1. Definición de tarea y datos que voy a utilizar

La tarea en cuestión es analizar los datos que me proporciona Model Fitness en el dataset 'gym_churn_us_csv' y elaborar una estrategia de retención de clientes, siguiendo los objetivos planteados anteriormente.

## Etapa 2. Obtener los datos

Los descargó de la plataforma y los importo a mi hoja de trabajo con el comando read_csv de pandas.

## Etapa 3. Análisis EDA

Utilicé librerias:
- Pandas
- Matplotlib
- Seaborn

Revisando los promedios y creando histogramas comparando la variable objetivo con algunas características para ver la relación entre si el cliente cancela su membresía o sigue activo en el gimnasio noté que la mayoría de las características tienen fuerte relación que la variable objetivo, y con una matriz de correlación que visualizé con un mapa de calor pude concluir que es aún más probable que el cliente siga activo dependiendo de la edad y el periodo de tiempo por el cuál haya contratado su membresía en el momento de la inscripción. 

## Etapa 4. Construir un modelo para predecir la cancelación de usuarios

Utilicé libreria:
- sklearn

Primero dividí los datos del conjunto de entrenamiento y validación utilizando la función train_test_split() para luego entrenar el módelo con:
- Regresío Logística: Utilicé tres características (Periodo de membresía = 'contract_period', Edad = 'age', Tiempo en el gimnasio = 'lifetime') que consideraba las más influyentes para afectar la decisión de irse o quedarse en el gimnasio, me dió un recall = 78% y una precisión = 79% la cual consideré baja ya que dejar sin identificar un 22% más de clientes que se pueden ir sin siquiera hacer el intento de retenerlos es algo considerable.
- Bosque Aleatorio: Aquí utilicé todas las características disponibles (13) y logré aumentar el recall al 82% sin trade-off con precisión que subió a 83% y un 89% de clasificación correcta de todos los clientes.
En conclusión: El modelo de Bosque Aleatorio nos arroja resultados más confiables y eficientes.

## Etapa 5. Creé clusters

Utilicé libreria:
- sklearn

En esta etapa, ignoré por completo los resultados y conclusiones obtenidas de los pasos anteriores para poder crear los clusters correctamente, ya que hay que recordar que los clusters sirven cuando no tienes una variable objetivo definida y no conoces las relaciones entre tus características.
Entonces, para crear mis clusters estandaricé los datos con sklearn.preprocessing --> StandardScaler, después cree una matriz de distancia con la función linkage() y la visualicé con un dendograma para identificar el número óptimo de clusters de mis datos de acorde a los colores, lo cuál me dió 5. 
Por ultimo, entren el modelo de clustering con el algortimo K-means y predige los clústeres de clientes. Al mirar los valores de churn de los clientes noté que el cluster 4 tenía un 97% de clientes que han cancelado su membresía, lo cuál comprobé al trazar las distribuciones de características para los clusters en digramas de cajas y calcular la tasa de cancelación de estos mismos.

## Conclusión general

Enfocar esfuerzos en mercadotecnía para clientes menores a 26 años y/o que hayan contratado un periodo de membresía de 2 mes o menos.
