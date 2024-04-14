# Detección de Enfermedad Cardiaca :heart:
Este proyecto de datos tiene como objetivo la detección de enfermedad cardiaca mediante el análisis de un conjunto de datos que contiene información sobre múltiples pacientes con diferentes grados de enfermedad o ausencia de la misma.

Esta tarea es de vital importancia, ya que la detección temprana de enfermedades cardiovasculares puede salvar o mejorar la calidad de vida de los pacientes. Desarrollar modelos precisos y eficientes puede ayudar a los profesionales médicos en la toma de decisiones clínicas y en la personalización de los tratamientos.

## Métricas de Evaluación :syringe:
El F1-score es una métrica de evaluación del rendimiento de un modelo de clasificación que combina las métricas de precisión y recall en una única medida de desempeño.

La precisión (precision) mide la proporción de verdaderos positivos sobre la suma de verdaderos positivos y falsos positivos, es decir, mide la proporción de casos positivos identificados correctamente sobre el total de casos positivos identificados.

El recall (sensibilidad) mide la proporción de verdaderos positivos sobre la suma de verdaderos positivos y falsos negativos, es decir, mide la proporción de casos positivos identificados correctamente sobre el total de casos positivos presentes en la muestra.

El valor del F1-score oscila entre 0 y 1, siendo 1 el valor óptimo que indica una predicción perfecta del modelo. En general, cuanto mayor sea el valor del F1-score, mejor será el rendimiento del modelo para clasificar correctamente los casos positivos y negativos. El F1-score es particularmente útil cuando las clases están desequilibradas en la muestra, ya que combina la precisión y el recall para proporcionar una evaluación más equilibrada del rendimiento del modelo.

El F1-score se calcula como la media armónica de la precisión y el recall.

## Dataset :moyai:
El conjunto de datos utilizado contiene información clínica y biométrica de pacientes, así como los resultados de pruebas médicas relevantes para la detección de enfermedades cardiovasculares. El objetivo es entrenar un modelo de aprendizaje automático que pueda predecir la presencia de enfermedad en el corazón basándose en estas características.

Con este proyecto, buscamos contribuir a mejorar la detección temprana de enfermedades cardiovasculares y, en última instancia, la atención y el tratamiento de los pacientes afectados.






--------------------------------        README MIGUEL        -------------------------------------

## DIA 1

0. He ejecutado el csv del dataset general
1. He convertido todo el dataset a string
2. He convertido todos los strings de NAs a NAs de NUMPY
3. He hecho una division de las variables numéricas y categóricas del dataset
4. Con el SimpleImputer he imputado los valores faltantes usando la MEDIA para las variables numéricas y el valor mas repetido (MODA) para las variables categóricas
----------------------------------------------------------------------------------------------------
1. TRY 4 - Con un Random Forest 0.52173
2. TRY 5 - Con un SVM 0.55978 


## DIA 2

1. He escalado las varibles continuas mediante el escalador Min-Max
2. He codificado las varibles categóricas mediante la técnica de one-hot
----------------------------------------------------------------------------------------------------
1. TRY 9 - Es un error de try, se me olvidó escalar la variable de la edad
2. TRY 10 - Con un Random Forest 0.57065


## DIA 3

1. He seguido todo del TRY 10, solo he cambiado en la limpieza de los datos la manera de convertir los NAs combinando en las variables numéricas la media en algunas y la mediana en otras dependiendo del valor que me habían dado los coeficientes de asimetría. Aunque en los dos intentos ha ido a peor.
----------------------------------------------------------------------------------------------------
1. TRY 16 - Con un Random Forest 0.55434    (Mean: 'trestbps', 'thalach', 'chol'   -   Median: 'oldpeak', 'age')
2. TRY 17 - Con un Random Forest 0.53804     (Mean: 'trestbps', 'thalach', 'age'   -   Median: 'oldpeak', 'chol')
3. TRY 18 - Con un Random Forest 0.55434    (Mean: 'trestbps', 'thalach', 'age', 'chol'   -   Median: 'oldpeak')


## DIA 4

1. Se acababa el tiempo del día y tiré un XG Boost a ver cuanto daba con la limpieza del one-hot y el escalado de las variables continuas.
----------------------------------------------------------------------------------------------------
1. TRY 21 - Con un XG Boost 0.52173


## DIA 5

1. He seguido todo del try 10 (se me olvidó escalar la variable "age").
----------------------------------------------------------------------------------------------------
1. TRY 26 - Con un Random Forest 0.55434 --> He cambiado los ceros de la variable "chol" por su media.
2. TRY 28 - Con un Random Forest 0.54347 --> He cambiado los ceros de la variable "chol" y los ceros y número negativos de la variable "oldpeak" por sus medias.
   
   
## DIA 6

1. He seguido todo del try 10 (ya estando bien escalada la variable "age").
----------------------------------------------------------------------------------------------------
1. RY 31 - Con un Random Forest 0.54891 --> He cambiado los ceros de la variable "chol" por su media.
2. TRY 32 - Con un Random Forest 0.54347 --> He cambiado los ceros de la variable "chol" y los ceros y número negativos de la variable "oldpeak" por sus medias.


## DIA 7

1. He estado hiperparametrizando los modelos Random Forest y XG Boost para estas situaciones:
   - Convirtiendo en nan los 0.0 de “chol” + Convirtiendo en nan los 0.0 y los valores negativos de “oldpeak”
   - Convirtiendo en nan los 0.0 de “chol” 
   - Sin convertir ni “chol” ni “oldpeak”
He acabado probando los dos intentos en los cuales más alto me salía el f1-score:
----------------------------------------------------------------------------------------------------
1. TRY 44 - Con un Random Forest 0.54891 (Convirtiendo en nan los 0.0 de “chol” + Convirtiendo en nan los 0.0 y los valores negativos de “oldpeak”)
Mejores hiperparámetros encontrados: {'max_depth': None, 'max_features': sqrt, 'min_samples_leaf': 1, 'min_samples_split': 2, 'n_estimators': 100}
Accuracy del modelo: 0.54891
F1-score del modelo: 0.70877

2. TRY 45 - Con un Random Forest 0.54347 (Convirtiendo en nan los 0.0 de “chol”)
Mejores hiperparámetros encontrados: {'max_depth': 20, 'max_features': 'sqrt', 'min_samples_leaf': 1, 'min_samples_split': 5, 'n_estimators': 50}
Accuracy del modelo: 0.51630
F1-score del modelo: 0.6810


## DIA 8 

1. He cogido el try.ipynb de Paco ya que habia sacado el mejor intento hasta la fecha (TRY 56 - 0,60326) y he ido modificando pequeñas cosas porque nos quedábamos sin tiempo para lanzar los intentos diarios:
----------------------------------------------------------------------------------------------------
1. TRY 59 - Con un CatBoost 0.59239 --> Lo mismo que el de Paco, pero he metido todas las variables desde el principio.

2. TRY 60 - Con un CatBoost 0.56521 --> Lo mismo que el de Paco, pero he metido en el modelo los parámetros del TRY 56.

3. TRY 61 - Con un CatBoost 0.55434 --> Lo mismo que el de Paco, pero he usado y metido en el modelo los parámetros de que me ha dado RandomSearch en vez de GridSearch.

3. TRY 61 (segundo) - Con un CatBoost 0.57608 --> Lo mismo que el de Paco, pero he usado para la variables categóricas One-Hot en vez de OrdinalEncoder.


## DIA 9

1. Me he dedicado únicamente a modificar los parámetros del TRY 56 (0,60326):
----------------------------------------------------------------------------------------------------
1. TRY 64 - Con un CatBoost 0.57065 

2. TRY 65 - Con un CatBoost 0.59782 

3. TRY 66 - Con un CatBoost 0.60326 --> El único cambio que hice respecto al TRY 56 es que los nan de la variable "thalach" los cambio por la media pero desde el trozo de código en el que decimos qué variable es numérica y cual es categórica, en vez de calcular la media con una función y unirla como se hacía en el TRY 56.
Parámetros utilizados: {'depth': 8, 'iterations': 20, 'l2_leaf_reg': 3, 'learning_rate': 0.09} 

4. TRY 67 - Con un CatBoost 0.59239 --> Me salía mejor al hiperparametrizar, pero luego dio menos score al meterlo en el Kaggle.


## DIA 10

1. Me he dedicado a hcaer cambios en la manera de limpiar los datos del TRY 66 (0,60326):
----------------------------------------------------------------------------------------------------
1. TRY 78 - Con un CatBoost 0.57065 --> Cree una varibale nueva que era agrupación por clusters, pero funcionó mal.

2. TRY 83 - Con un CatBoost 0.54347 --> En la limpieza elimino las variable "ca" y "thal" debido a la gran cantidad de datos nulos, y también categorizo la variable "oldpeak" ya que tenía una gran cantidad de ceros.