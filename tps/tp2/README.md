# Trabajo Práctico 2 - Machine Learning Cátedra Argerich

[Competencia: Binary Classification of VPN Proxy IP Address.](https://www.kaggle.com/competitions/vpn-classification/overview)


Posible balanceo de datos:

```python
# El data set se encuentra desbalanceado, por lo que se procede a realizar un balanceo de los datos.
# Para ello se utiliza la técnica de SMOTE (Synthetic Minority Oversampling Technique).
# Se utiliza la librería imbalanced-learn para realizar el balanceo de los datos.
# https://imbalanced-learn.org/stable/
from imblearn.over_sampling import SMOTE

# Se separan las variables independientes de la variable dependiente
X = df_train.drop(['label'], axis=1)
y = df_train['label']

# Se aplica la técnica de SMOTE para balancear los datos
smote = SMOTE(random_state=42)
X, y = smote.fit_resample(X, y)

# Se crea un nuevo data frame con los datos balanceados
df_train_balanced = pd.DataFrame(X, columns=df_train.columns.drop(['label']))
df_train_balanced['label'] = y

# Se verifica que el data frame se encuentre balanceado
df_train_balanced['label'].value_counts()

# Se grafica la distribución de clases del data frame balanceado
class_counts = df_train_balanced['label'].value_counts()

# Crear un gráfico de barras apiladas con colores atractivos
fig, ax = plt.subplots(figsize=(8, 6))
```