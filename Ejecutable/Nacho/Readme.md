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

### DIA 3

1. 22 TRY con un Random Forest , al que le he añadido la categorizacion de la variable Age por tramos de Edad
2. 23 TRY con un Random Forest , al que le he añadido la categorizacion todas las variables numericas y dropeo las que he categorizado
3. 24 TRY con un Random Forest , y NO dropeo las que he categorizado

### DIA 4

1. 27 TRY con un Random Forest, cojo la limpieza de Miguel del 0.570 que estaba normalizada y le meto mis correlaciones
2. 29 TRY con un Random Forest, con una nueva limpieza pruebo sin correlaciones
3. 30 TRY con un Random Forest, y ahora CON correlaciones