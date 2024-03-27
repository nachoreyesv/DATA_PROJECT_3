### DIA 1

0. He ejecutado el csv del dataset general
1. He convertido todo el dataset a string
2. He convertido todos los strings de NAs a NAs de NUMPY
3. He hecho una division de las variables numéricas y categóricas del dataset
4. Con el SimpleImputer he imputado los valores faltantes usando la mediana para las variables numéricas y el valor mas repetido (moda) para las variables categóricas

1. Primer TRY con un Random Forest 0.51630
2. Segundo TRY con un SVM 0.55434 POLE
3. Tercer TRY con un KNN 0.45652

### DIA 2

1. He hecho una regresion logistica para saber que variables son las que mas relacion o mas inluencia tienen en la variable label
2. Luego he creado una variable llamada score_by_correlation que es la suma de las correlaciones de cada variable de cada observacion

1. 11 TRY con un Random Forest 0.57608
2. 12 TRY con un Ensemble de Random Forest, Xgboost, Regresión Logística y Knn 0.53804