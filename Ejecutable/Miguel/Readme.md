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
