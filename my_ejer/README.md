Apunte
# NPL

## Tokenización
```python
from nltk import word_tokenize
import nltk
nltk.download('punkt')
nltk.download('wordnet')
nltk.download('stopwords') # Capaz antes de usar nltk les pide que descarguen estas cositas
```
Funciones: <br>
| Función | Descripción | Tipo |Import|
| --- | --- | --- | --- |
| word_tokenize() | Tokeniza un texto | Tokenización | from nltk import word_tokenize|
| PorterStemmer() | Stemming | Normalización | from nltk.stem.porter import PorterStemmer |
| WordNetLemmatizer() | Lemmatization | Normalización | from nltk.stem import WordNetLemmatizer |
| stopwords.words() | Stopwords | Normalización | from nltk.corpus import stopwords |

## Term Frequency (Count Vectorizer)
```python
sklearn.feature_extraction.text.CountVectorize
class sklearn.feature_extraction.text.CountVectorizer()
```
Las funciones `fit()`, `transform()`, y `fit_transform()` tienen diferentes propósitos:

1. `fit(raw_documents[, y])`: Esta función se utiliza para aprender el vocabulario de los documentos que se le pasan como argumento. El vocabulario aprendido se utiliza luego para vectorizar los documentos¹².

2. `transform(raw_documents[, y])`: Esta función se utiliza para convertir los documentos en vectores utilizando el vocabulario que se aprendió previamente con la función `fit()`. No aprende ningún nuevo vocabulario¹².

3. `fit_transform(raw_documents[, y])`: Esta función combina las funcionalidades de `fit()` y `transform()`. Primero aprende el vocabulario de los documentos y luego los convierte en vectores¹².

Es importante notar que no debes usar `fit_transform()` en los datos de prueba porque, cuando ajustas un modelo, el modelo aprende las reglas de clasificación basadas en los valores de las características que le proporcionas. Si estas reglas se van a aplicar para clasificar el conjunto de prueba, entonces necesitas asegurarte de que las características de prueba se calculen de la misma manera usando el mismo vocabulario. Si el vocabulario de las características de entrenamiento y las características de prueba es diferente, entonces las características realmente no tendrán sentido ya que reflejarán un vocabulario que es separado del que se entrenó el documento.

