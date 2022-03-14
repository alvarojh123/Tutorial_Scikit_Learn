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


AQUI COMECEI A REPORTAR TUDO 

#### MANIPULANDO (APENAS) VARIÁVEIS CATEGÓRICAS

Temos dois tipos de variáveis: Numéricas e Categóricas. 


```python
import pandas as pd

# Importar dados
adult_census = pd.read_csv('../datasets/adult-census.csv')
# Eliminar uma coluna duplicada, usando drop
adult_census = adult_census.drop(columns='educations_num')

# Definir a data e o target

targe_name = 'class'
target = adult_census[target_name]

data = adult_census.drop(columns=target_name)
```

##### Identificar variáveis categóricas

Há duas formas de identificar as variáveis categóricas, sendo manual e automática.


A forma manual:

```python

data.dtypes # int64 = inteiros / object = Strings

```

A forma automática

```python

from sklearn.compose import make_column_selector as selector

categorical_columns_selector = selector(dtype_include = object)
categorical_columns = categorical_ columns_selector(data)

```
Logo, criamos a data_categorical contendo apenas os dados categóricos.

```python

data_categorical = data[categorical_columns]
```


##### Codificar dados categóricos


Método OrdinalEncoder: Substitui cada categoria por um número inteiro (arbitrário).


```python

from sklearn.preprocessing import OrdinalEncoder

encoder = OrdinalEncoder()
data_encoded = encoder.fit_transform(data_categorical)

# Para ver as categorias
encoder.categories_

```


Método OneHotEncoder: Cada categoria é convertida numa coluna. Em cada columna, cada amostra recebe o
valor de 1 (presença) ou 0 (ausência). 

```python

from sklearn.preprocessing import OneHotEncoder

encoder = OneHotEncoder(sparse=False)
data_encoded = encoder.fit_transform(data_categorical)

# Converter a pandas dataframe

columns_encoded = encoder.get_feature_names_out(data_categorical.columns)
pd.DataFrame(data_encoded, columns = columns_encoded).head()

```

Nota: OneHotEncoder é recomendado para modelos lineares. OrdinalEncoder es recomendado para 
modelos baseados em arvores. 

##### Modelagem



```python
from sklearn.pipeline import make_pipeline
from sklearn.linear_model import LogisticRegression

# Construir o pipeline
model = make_pipeline(OneHotEncoder(handle_unknow="ignore"), LogisticRegression(max_iter=500))

```

##### Cross-validation


```python
from sklearn.model_selection import cross_validate

cv_results = cross_validate(model, data_categorical, target)

scores = cv_results['test_score']
print(f"A acuracia é {scores.mean():.3f} +/- {scores.std():.3f}")
#

```

#### MANIPULANDO VARIÁVEIS NUMÉRICAS E CATEGÓRICAS

```python
import pandas as pd

# Importar dados
adult_census = pd.read_csv('../datasets/adult-census.csv')
# Eliminar uma coluna duplicada, usando drop
adult_census = adult_census.drop(columns='educations_num')

# Definir a data e o target

targe_name = 'class'
target = adult_census[target_name]

data = adult_census.drop(columns=target_name)
```

Selecionamos baseados nos tipos de dados.

```python

from sklearn.compose import make_column_selector as selector

numerical_columns_selector   = selector(dtype_exclude=object)
categorical_columns_selector = selector(dtype_include=object)

numerical_columns   = numerical_columns_selector(data)
categorical_columns = categorical_columns_selector(data)

```



```python

from sklearn.preprocessing import OneHotEncoder, StandardScaler


```



