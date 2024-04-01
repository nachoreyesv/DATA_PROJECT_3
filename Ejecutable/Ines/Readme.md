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




