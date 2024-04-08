# DIA 25/03

- Creo mi carpeta e incluyo otro archivo main (ines_main) porque quería hacer algunos cambios más.
  
## Limpieza Nº 1:

- En el archivo pruebas he probado a imputar por regresión todos los valores nulos del dataset (sin hacer ninguna distinción entre variables por el momento).
  
- Divido en train, val y test (70% - 10% - 20%)
  
- Normalizo los datos.
  
- Pruebo un **árbol de decisión** sin definir la profundidad:
  - F1-score validación: 0.4002638626339004
  
  **TRY7**
  - F1-score en kaggle: 0.47282
  

- Pruebo un clasificador **KNN** haciendo un GridSearch para k, el mejor valor de k = 9:
  - F1-score validación: 0.43123673596373296
  
  **TRY8**
  - F1-score en kaggle: 0.44021
  

- Pruebo otro **KNN**, esta vez con k = 4:
  - F1-score validación: 0.4973919351513467
  

- Pruebo un clasificador **SVM** haciendo un GridSearch para C y kernel. Mejores hiperparámetros: {'C': 10, 'kernel': 'linear'} 
  - F1-score validación: 0.4936275222609038
  

- Pensamientos de mejora:
    - Dividir variables según su tipo para imputarlas.
    - Al separar los sets en entrenamiento y validación, encontrar la forma de que tengan la misma estructura y distribución que los de test.


# DIA 31/03

## Limpieza Nº 2: 

- Variables continuas imputadas por regresión y variables categóricas imputadas por KNN
  
- División de sets
  
- Normalización
  
- Todos los parámetros buscados con GridSearch

- **KNN** con k=2
  - F1-score de validación: 0.4649427010440172

- **SVM** con C=10 y kernel=linear
  - F1-score de validación: 0.49980905462947056

- **Random Forest** con 'max_depth': 10, 'n_estimators': 200
  - F1-score de validación: 0.5267261537670881


- **XGBoost** con 'learning_rate': 0.1, 'max_depth': 1
  - F1-score de validación: 0.5204226855475699


- **XGBoost** con 'learning_rate': 0.1, 'max_depth': 11
  - F1-score de validación: 0.5110747594575802


- **Naive Bayes**
  - F1-score de validación: 0.5380419518747414
  
## Limpieza Nº 3:

Los '0' de la variable 'CHOL' han sido tratados como NaNs: Variables continuas imputadas por regresión y variables categóricas imputadas por KNN

El procedimiento es igual que en la Limpieza Nº 2. EL F1-score de validación de todos los modelos es el mismo que en la limpieza Nº 2 excepto para el Random Forest:

- **Random Forest** con 'max_depth': 20, 'n_estimators': 200 (parámetros gridsearch)
  - F1-score de validación: 0.5450415115920516

- **Random Forest** con 'max_depth': 10, 'n_estimators': 200
  - F1-score de validación: 0.5434492812679145
  
- **Naive Bayes**
  - F1-score de validación: 0.5380419518747414
  
  **TRY30 (2.0)**
  - F1-score en kaggle: 0.54347


# DIA 01/04

- Pruebo a añadir un PCA a la Limpieza Nº 3. 

### 1ª PRUEBA
- PCA con 3 componentes
  
- **Naive Bayes**
  - F1-score de validación: 0.5033081285444234
  
- **Random Forest** con 'max_depth': None, 'n_estimators': 50
  - F1-score de validación: 0.5224004084545164
  
  **TRY33**
  - F1-score en kaggle: 0.52717
  


### 2ª PRUEBA
- PCA con 6 componentes

- **Random Forest** con 'max_depth': 10, 'n_estimators': 50
  - F1-score de validación: 0.4773618829682903


## LIMPIEZA Nº 4:

Corrijo el error de la limpieza Nº 3. Había cogido el dataframe con los 0 de 'chol' en lugar del que ya los tenía como Nan :(. Por lo demás todo igual.

- **KNN** 
  - F1-score de validación: 0.5537183145878799

- **SVM** 
  - F1-score de validación: 0.46270176720573813

- **Random Forest**
  - F1-score de validación: 0.5230518200735179

- **XGBoost**
  - F1-score de validación: 0.5502044481067173

- **Naive Bayes**
  - F1-score de validación: 0.5055874422569836
  
KNN, XGBOOST y RAANDOM FOREST mejoran, los demás van a peor.

Pruebo a hacer PCA otra vez con varios números de componentes pero ningún modelo mejora respecto a los modelos con las variables "sin modificar".


Pruebo a crear un **SET FALSO DE TEST** de forma que tengo 60% train, 10% validación, 10% test FASLO y 20% del test original. 

Sigo el mismo procedimiento de la limpieza Nº 4, con normalización incluida.

Casi todos los modelos mejoran en validación y los porcentajes de aciertos (respecto al set de test FALSO) son bastante buenos:

- **KNN** 
  - F1-score de validación: 0.462986295033371
  - Porcentaje de aciertos: 56.52%

- **SVM** 
  - F1-score de validación: 0.5261034255599473
  - Porcentaje de aciertos: 54.35%

- **Random Forest**
  - F1-score de validación: 0.5997578332986716
  - Porcentaje de aciertos: 51.09%

- **XGBoost**
  - F1-score de validación: 0.5581477386676265
  - Porcentaje de aciertos: 58.70%

- **Naive Bayes**
  - F1-score de validación: 0.5155824443867921
  - Porcentaje de aciertos: 55.43%


# DIA 02/04

He cogido el código de las correlaciones del TRY 11 pero cambiando la imputación de NaNs como en la limpieza Nº 4. 

- **Random Forest**
  **TRY 43**
  - F1-score en kaggle: 0.52173 :( .


# DIA 04/04
Limpio todas las variables a saco, considerando que aquellos valores que están por encima del 3r cuartil + (1.5 * IQR) o por debajo del 1r cuartil - (1.5 * IQR) representan valores atípicos y los reemplazo por NaNs.

Los NaNs son imputados por KNN en variables categóricas y por regresión en variables continuas. 

Separo los sets de forma que tengan la misma distribución, normalizo y empiezo con los modelos. Aquí hago pruebas sin añadir pesos a la variable 'label' y después añadiendolos para ver la diferencia.


- **SVM SIN PESOS** 
  - F1-score de validación: 0.4908787113684352  (48 aciertos según la matriz de confusión)


- **SVM CON PESOS** 
  - F1-score de validación: 0.46763718553044614 (47 aciertos)


- **Random Forest SIN PESOS**
  - F1-score de validación: 0.5269615346349004 (51 aciertos)
  **TRY 63**
  - F1-score en kaggle: 0.52717 (No predice 4s)


- **Random Forest CON PESOS**
  - F1-score de validación: 0.4861310858365415 (48 aciertos)
  **TRY 54_02**
  - F1-score en kaggle: 0.48913 (Predice cuatro 4s)


- **XGBoost SIN PESOS**
  - F1-score de validación:0.5091899008867443 (49 aciertos)
  

- **XGBoost CON PESOS**
  - F1-score de validación: 0.5391887389638513 (51 aciertos)
  **TRY 62**
  - F1-score en kaggle: 0.45652 (Predice ocho 4s)


- **Naive Bayes**
  - F1-score de validación: 0.5251517607424357