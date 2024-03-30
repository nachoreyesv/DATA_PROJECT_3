## TO DO

## INTENTO 1
0. He ejecutado el csv del dataset general
1. He convertido todos los strings de NAs a NAs de NUMPY
2. He hecho una division de las variables numéricas y categóricas del dataset
3. Con el SimpleImputer he imputado los valores faltantes usando la media para las variables numéricas y el valor mas repetido (moda) para las variables categóricas
4. He separado train en train y validación y aplicado SMOTE sobre el train.
5. Grid y selección del mejor modelo:  Random Forest
   
## TRY
Random Forest 0.54891

## INTENTO 2 
0. He ejecutado el csv del dataset general
1. He convertido todos los strings de NAs a NAs de NUMPY
2. He hecho una division de las variables numéricas y categóricas del dataset
3. Con el SimpleImputer he imputado los valores faltantes usando la media para las variables numéricas y el valor mas repetido (moda) para las variables categóricas // **CON ALGUNAS EXCEPCIONES**
4. He parametrizado la variable CHOL para que el output sea categórico 
5. **chol**
   > **Colesterol sérico** Normal : Menos de 200 mg/dl , Límite superior del rango normal: Entre 200 y 239 mg/dl , Alto: 240 mg/dl o más, los nulls o 0 se tratan como una categoría a parte.
6. He creado un nuevo posible valor en la variable THAL que corresponde a los valores NaN
7. He estandarizado todas variables cuantitativas continuas.
8. He separado train en train y validación y aplicado SMOTE sobre el train.
9. Grid y selección del mejor modelo : Random Forest
    
## TRY
Random Forest 0.53260

## INTENTO 3
0. He ejecutado el csv del dataset general
1. He convertido todos los strings de NAs a NAs de NUMPY
2. He hecho una division de las variables numéricas y categóricas del dataset
3. He calculado la media ral sin NaNs para la variable TALACH y he rellenado los NaNs con esta.
4. He parametrizado la variable CHOL y TRESBPS para que el output sea categórico
5. He creado  umbrales para la variable **trestbps**
   > **Presión arterial sistólica**  Normal:  Menos de 120  mm Hg , Elevada: 120-129 mmHg , Presión arterial alta: 130 mm Hg o más, los nulls se tratan como una categoría a parte
6. Con el SimpleImputer he imputado los valores faltantes usando la media para las variables numéricas y el valor mas repetido (moda) para las variables categóricas // **CON ALGUNAS EXCEPCIONES** 
7.  He creado  umbrales para la variable **chol**
   > **Colesterol sérico** Normal : Menos de 200 mg/dl , Límite superior del rango normal: Entre 200 y 239 mg/dl , Alto: 240 mg/dl o más, los nulls o 0 se tratan como una categoría a parte.
8. He creado un nuevo posible valor en la variable THAL que corresponde a los valores NaN
9. He creado una nueva varibale a raíz de la variable TALACH, SEX Y AGE que categorizo en función de esta tabla ![.](fps.jpg)
10. He estandarizado todas variables cuantitativas continuas que quedan (AGE y OLDPEAK).
11. He separado train en train y validación y aplicado SMOTE sobre el train. 
12. Grid y selección del mejor modelo : Random Forest
    
## TRY
Random Forest 0.54347

## INTENTO 4 
1. Lo mismo que el 3 pero estandarizando las variables categóricas de la siguiente forma :
   1.  Ordinal encoding en las variables slope, ca y thal y restecg. 
   2.  Count encoding en las variables chol ,**thalach_cat** , trestbps y cp.
   


   



## IDEAS
1.CLASSWEIGHTS

| Categoria   | Entradas | Porcentaje | Corresponderían en 184 entradas |
|-------------|----------|------------|---------------------------------|
| Categoria 0 | 327      | 44.67%     | 82                              |
| Categoria 1 | 156      | 21.31%     | 39                              |
| Categoria 2 | 108      | 14.75%     | 27                              |
| Categoria 3 | 107      | 14.62%     | 27                              |
| Categoria 4 | 34       | 4.64%      | 9                               |

   