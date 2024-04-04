### DIA 1

0. He ejecutado el csv del dataset general
1. He convertido todo el dataset a string
2. He convertido todos los strings de NAs a NAs de NUMPY
3. He hecho una division de las variables numéricas y categóricas del dataset
4. Con el SimpleImputer he imputado los valores faltantes usando la MEDIA para las variables numéricas y el valor mas repetido (MODA) para las variables categóricas
----------------------------------------------------------------------------------------------------
1. TRY 4 - Con un Random Forest 0.52173
2. TRY 5 - Con un SVM 0.55978 


### DIA 2

1. He escalado las varibles continuas mediante el escalador Min-Max
2. He codificado las varibles categóricas mediante la técnica de one-hot
----------------------------------------------------------------------------------------------------
1. TRY 9 - Es un error de try, se me olvidó escalar la variable de la edad
2. TRY 10 - Con un Random Forest 0.57065


## DIA 3

1. He seguido todo del TRY 10, solo he cambiado en la limpieza de los datos la manera de convertir los NAs convinando en las varibales numéricas la media en algunas y la mediana en otras dependiendo del valor que me habían dado los coeficientes de asimetría. Aunque en los dos intentos ha ido a peor.
----------------------------------------------------------------------------------------------------
1. TRY 16 - Con un Random Forest 0.55434    (Mean: 'trestbps', 'thalach', 'chol'   -   Median: 'oldpeak', 'age')
2. TRY 17 - Con un Random Forest 0.53804     (Mean: 'trestbps', 'thalach', 'age'   -   Median: 'oldpeak', 'chol')