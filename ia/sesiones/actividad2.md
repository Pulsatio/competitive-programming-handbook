# Actividad 2 — Clasificación con K-NN y Regresión Logística (Titanic)

**Objetivo:** aprender a preparar datos, entrenar y comparar dos clasificadores (K-NN y Regresión Logística) para predecir supervivencia en el dataset Titanic.

### Dataset

Usaremos una versión del dataset Titanic en formato CSV que el estudiante descargará o colocará en `data/titanic.csv`.
La plantilla muestra cómo cargar los datos con `pandas` sin depender de `seaborn`.

### Objetivo de la plantilla

Deja un ejemplo mínimo de carga y limpieza de datos con `pandas` y pide a los estudiantes que:

- Construyan dos modelos (Regresión Logística y K-NN) usando `scikit-learn`.
- Visualicen los datos y las fronteras de decisión (usar 2 features para visualización 2D).
- Justifiquen la elección de parámetros (por ejemplo `k` en K-NN, `C`/regularización en logística) y qué métricas consideran.

### Cómo cargar datos (plantilla)

```python
import pandas as pd

# Cargar directamente desde la URL pública (alternativa a un CSV local)
url = "https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv"

# Cargar con pandas
df = pd.read_csv(url)

# Inspección rápida
print(df.shape)
print(df.columns)
print(df.head())

# Ejemplo de limpieza mínima (plantilla)
# - Seleccionar columnas relevantes
features = ['pclass', 'sex', 'age', 'sibsp', 'parch', 'fare', 'embarked']
df = df[features + ['survived']]

# - Imputar/filtrar según criterio del alumno
# df['age'] = df['age'].fillna(df['age'].median())

# A partir de aquí: crear X, y, preprocesamiento, split, y entrenar modelos.
```

### Tarea (lo que deben entregar)

1. Código que carga `data/titanic.csv` usando `pandas.read_csv` y realiza limpieza mínima.
2. Implementación de dos modelos con `scikit-learn`: `LogisticRegression` y `KNeighborsClassifier`.
3. Visualizaciones: distribución de clases, gráficos de las features elegidas, y fronteras de decisión 2D (usando 2 features).
4. Evaluación: reportar accuracy, precision, recall, F1 y ROC-AUC para ambos modelos.
5. Explicación escrita (breve): por qué eligieron los hiperparámetros (p. ej. `k`, regularización), qué trade-offs consideran y cómo afectaron las decisiones al rendimiento.

### Plantilla mínima de entrenamiento (esqueleto)

```python
# Después de cargar y limpiar df
X = df[features]
y = df['survived']

from sklearn.model_selection import train_test_split
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler, OneHotEncoder
from sklearn.compose import ColumnTransformer
from sklearn.impute import SimpleImputer
from sklearn.linear_model import LogisticRegression
from sklearn.neighbors import KNeighborsClassifier

# Preprocesamiento sugerido (editable)
num_features = ['age', 'sibsp', 'parch', 'fare']
cat_features = ['pclass', 'sex', 'embarked']

# ColumnTransformer, Pipelines y split (estudiante completa)

# Modelo 1: LogisticRegression
# Modelo 2: KNeighborsClassifier

# Entrenar, predecir y evaluar

# Visualizar fronteras 2D usando dos features escaladas
```

### Preguntas

- ¿Qué modelo obtiene mejor precisión y por qué? .
- ¿Cómo afecta el valor de `k` en K-NN? Prueba varios `k`.
- ¿Qué pasa si eliminas `fare` o `age`? ¿Qué características son más importantes?
- Experimenta con imputaciones distintas y con selección de variables.
