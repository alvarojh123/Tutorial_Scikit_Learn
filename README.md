# Tutorial_Scikit_Learn
Informações importantes para aprender machine learning com  Scikit Learn



#### Carregar dados com pandas

```python
import pandas as pd
data_set = pd.read_csv("dataset")

```

## Primeiro modelo com ScikitLearn

### Carregar dados

### Separar dados em features (X) e target (y)



### 



#### Manipulando variáveis categóricas

Temos dois tipos de variáveis: Numéricas e Categóricas.

```python

# Importar dados


# Definir a data e o target

targe_name = 'class'
target = adult_census[target_name]
data = adult_census


```

##### Codificar dados categóricos

Método OrdinalEncoder: Substitui cada categoria por um número inteiro (arbitrário).


```python

```


Método OneHotEncoder: Cada categoria é convertido numa coluna. Cada amostra recebe o
valor de 1 (presença) ou 0 (ausẽncia).

```python
from sklearn.preprocessing import OneHotEncoder

encoder = OneHotEncoder(sparse=False)
data_encoded = encoder.fit_transform(data_categorical)


```




