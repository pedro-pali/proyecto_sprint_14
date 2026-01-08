# proyecto_sprint_14

## Step 1. Análisis EDA

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