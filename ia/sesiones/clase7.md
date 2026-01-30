# Clase 7 — Modelos de Aprendizaje Supervisado

## ¿Qué es el aprendizaje supervisado?

El aprendizaje supervisado es una rama del aprendizaje automático en la que disponemos de un conjunto de datos etiquetado ((x*i, y_i)), donde cada entrada $x_i$ tiene una etiqueta o salida conocida $y_i$. El objetivo es aprender una función $f*\theta(x)$ parametrizada por $\theta$ que aproxime la relación entre entradas y salidas, de modo que para nuevas entradas $x$ podamos predecir $y$. El proceso se reduce a minimizar una función de pérdida empírica:

$$
R_n(\theta)=\frac{1}{n}\sum_{i=1}^n L\big(y_i, f_\theta(x_i)\big)
$$

donde $L$ es una función de pérdida (por ejemplo, error cuadrático medio o log-loss).

## Modelos tratados en esta clase

- **Regresión Lineal:** explicación detallada más adelante.
- **Regresión Logística:** explicación detallada más adelante.
- **L1 & L2 Regularization:** técnicas para penalizar complejidad del modelo.
- **K-Nearest Neighbors (K-NN):** método basado en instancias y vecinos.
- **Decision Trees:** modelos basados en particiones recursivas.
- **Model Ensembles:** Gradient Boosting, Bagging, Random Forest — combinación de modelos para mejorar rendimiento.
- **Support Vector Machines (SVM):** clasificadores que maximizan el margen.
- **Practice:** sugerencias de ejercicios y datasets para practicar.

---

## Regresión Lineal

### Modelo

La regresión lineal modela la salida como una combinación lineal de las características:

$$
\hat{y} = f_\theta(x) = w^T x + b
$$

con parámetros $\theta = (w, b)$.

### Función de pérdida

Se usa frecuentemente el error cuadrático medio (MSE):

$$
L( y, \hat{y} ) = (y - \hat{y})^2
$$

La pérdida empírica es:

$$
J(w,b)=\frac{1}{n}\sum_{i=1}^n (y_i - w^T x_i - b)^2
$$

### Solución (forma cerrada)

Si representamos los datos con la matriz $X\in\mathbb{R}^{n\times d}$ (cada fila es $x_i^T$) y el vector $y\in\mathbb{R}^n$, la solución por mínimos cuadrados ordinarios es:

$$
w^* = (X^T X)^{-1} X^T y
$$

siempre que $X^T X$ sea invertible. Esto corresponde a minimizar $J(w,b)$ de forma exacta.

### Optimización (descenso de gradiente)

Para datasets grandes o cuando no es invertible, se usa descenso de gradiente (o variantes):

Gradientes:

$$
\nabla_w J = -\frac{2}{n} X^T (y - Xw - b\mathbf{1}),\quad
\nabla_b J = -\frac{2}{n} \sum_{i=1}^n (y_i - w^T x_i - b)
$$

### Regularización

- **Ridge (L2):** agrega $\lambda \|w\|_2^2$ a la pérdida. Solución cerrada:

$$
w^* = (X^TX + \lambda I)^{-1} X^T y
$$

- **Lasso (L1):** agrega $\lambda \|w\|_1$, favorece soluciones dispersas (sparse). Requiere optimizadores específicos.

Regularizar ayuda a reducir overfitting y a manejar colinealidad.

### Suposiciones y uso

- Linealidad: relación lineal entre características y la salida.
- Homocedasticidad y residuos no correlacionados para inferencia clásica.
- Aplicaciones: predicción de precios, regresión sobre series, modelos base para ingeniería de características.

---

### Ejemplo: Regresión Lineal con scikit-learn y gráfica

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression

# Datos sintéticos
rng = np.random.RandomState(0)
X = 2 * rng.rand(100, 1)
y = 4 + 3 * X.ravel() + rng.randn(100)

# Ajuste con scikit-learn
model = LinearRegression()
model.fit(X, y)

# Predicción para la línea
X_plot = np.linspace(0, 2, 100).reshape(-1, 1)
y_pred = model.predict(X_plot)

plt.figure(figsize=(6,4))
plt.scatter(X, y, label='datos')
plt.plot(X_plot, y_pred, color='red', label=f'regresión (slope={model.coef_[0]:.2f})')
plt.xlabel('x')
plt.ylabel('y')
plt.legend()
plt.title('Regresión Lineal - Ajuste y datos')
plt.show()
```

## Regresión Logística

### Modelo

La regresión logística modela la probabilidad de clase (binaria) mediante la función sigmoide:

$$
P(y=1\mid x)=\sigma(w^T x + b)=\frac{1}{1+e^{-(w^T x + b)}}
$$

La predicción binaria se obtiene comparando $p=\sigma(\cdot)$ con un umbral (habitualmente 0.5).

### Función de pérdida (Log-loss / Cross-entropy)

La pérdida por ejemplo es la entropía logística:

$$
L(y,p) = -\big[y\log p + (1-y)\log(1-p)\big]
$$

La función a minimizar es la suma sobre el dataset:

$$
J(w,b)= -\frac{1}{n}\sum_{i=1}^n \big[y_i\log \sigma(z_i) + (1-y_i)\log(1-\sigma(z_i))\big],\quad z_i=w^T x_i + b
$$

### Optimización

No existe solución cerrada; se usan métodos iterativos: descenso de gradiente, L-BFGS, Newton-Raphson o IRLS (Iteratively Reweighted Least Squares).

Gradiente para descenso por lotes:

$$
\nabla_w J = -\frac{1}{n} X^T (y - \sigma(Xw + b)),\quad \nabla_b J = -\frac{1}{n} \sum_{i=1}^n (y_i - \sigma(z_i))
$$

### Interpretación

- Las salidas son probabilidades; el cociente de probabilidades (odds) y el log-odds (logit) permiten interpretar coeficientes: un incremento unitario en $x_j$ cambia el log-odds en $w_j$.
- Muy usado cuando se requiere probabilidad calibrada y explicabilidad.

### Regularización

- **L2 (Ridge):** penaliza grandes pesos y evita overfitting.
- **L1 (Lasso):** produce sparsidad y selección de variables.

### Extensiones

- **Multiclase:** se adapta con softmax (multinomial logistic) o esquema one-vs-rest.
- **Calibración y métricas:** ROC-AUC, precisión/recall, F1.

---

### Ejemplo: Regresión Logística con scikit-learn y frontera de decisión

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.datasets import make_classification
from sklearn.linear_model import LogisticRegression

# Datos sintéticos 2D
X, y = make_classification(n_samples=300, n_features=2, n_redundant=0,
                           n_clusters_per_class=1, class_sep=1.2, random_state=0)

# Ajuste
clf = LogisticRegression(solver='lbfgs')
clf.fit(X, y)

# Grilla para la frontera
xx, yy = np.meshgrid(np.linspace(X[:,0].min()-1, X[:,0].max()+1, 200),
                     np.linspace(X[:,1].min()-1, X[:,1].max()+1, 200))
Z = clf.predict_proba(np.c_[xx.ravel(), yy.ravel()])[:, 1]
Z = Z.reshape(xx.shape)

plt.figure(figsize=(6,5))
plt.contourf(xx, yy, Z, levels=20, cmap='RdBu', alpha=0.6)
plt.scatter(X[:,0], X[:,1], c=y, cmap='bwr', edgecolor='k')
plt.title('Regresión Logística - Probabilidad y frontera de decisión')
plt.xlabel('x0')
plt.ylabel('x1')
plt.colorbar(label='P(y=1)')
plt.show()
```

## L1 & L2 Regularization (breve)

- **L2 (Ridge):** penaliza la suma de cuadrados de los parámetros, favorece soluciones con pesos pequeños pero no nulos.
- **L1 (Lasso):** penaliza la suma de valores absolutos y puede llevar a soluciones con coeficientes exactamente cero (selección de características).

Ambas se introducen añadiendo $\lambda R(w)$ a la función de pérdida.

## K-Nearest Neighbors (K-NN) (breve)

K-NN es un método no paramétrico que predice la etiqueta de una muestra según las etiquetas de sus $k$ vecinos más cercanos en el espacio de características (distancia Euclídea u otra). Simplicidad y buena performance en datasets pequeños, pero costoso en predicción para grandes volúmenes y sensible a la escala de las características.

### Ejemplo: K-NN con scikit-learn y frontera de decisión

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.datasets import make_moons
from sklearn.neighbors import KNeighborsClassifier

X, y = make_moons(n_samples=300, noise=0.25, random_state=0)

knn = KNeighborsClassifier(n_neighbors=7)
knn.fit(X, y)

xx, yy = np.meshgrid(np.linspace(X[:,0].min()-1, X[:,0].max()+1, 300),
                     np.linspace(X[:,1].min()-1, X[:,1].max()+1, 300))
Z = knn.predict(np.c_[xx.ravel(), yy.ravel()])
Z = Z.reshape(xx.shape)

plt.figure(figsize=(6,5))
plt.contourf(xx, yy, Z, cmap='Pastel2', alpha=0.6)
plt.scatter(X[:,0], X[:,1], c=y, cmap='bwr', edgecolor='k')
plt.title('K-NN (k=7) - Frontera de decisión')
plt.xlabel('x0')
plt.ylabel('x1')
plt.show()
```

## Decision Trees (breve)

Los árboles de decisión particionan recursivamente el espacio de entrada según condiciones en características (por ejemplo, $x_j < t$). Fáciles de interpretar, pueden sobreajustar sin poda. Se usan como base para ensamblados.

## Model Ensembles (breve)

- **Bagging:** entrena varios modelos (por ejemplo, árboles) en muestras bootstrap y promedia/vota (Random Forest es un caso de bagging con selección aleatoria de características).
- **Random Forest:** conjunto de árboles con mayor robustez y reducción de varianza.
- **Gradient Boosting:** construye modelos de forma secuencial corrigiendo errores residuales (Ej.: XGBoost, LightGBM, CatBoost).

## Support Vector Machines (SVM) (breve)

Los SVM construyen un hiperplano que separa clases maximizando el margen entre clases. Para clases no linealmente separables usan núcleos (kernels) que proyectan datos a espacios de mayor dimensión.

## Practice (sugerencias)

- Datasets: Iris, Boston (o alternativas modernas), Titanic, MNIST.
- Ejercicios:
  - Implementar regresión lineal por mínimos cuadrados y por descenso de gradiente.
  - Implementar regresión logística con gradiente y comparar con una librería (scikit-learn).
  - Probar K-NN y árboles, luego comparar con Random Forest y Gradient Boosting.

---

## Referencias rápidas

- Bishop, C. M. — Pattern Recognition and Machine Learning.
- Hastie, Tibshirani, Friedman — The Elements of Statistical Learning.

---

Archivo creado para la Clase 7: explicación general, lista de modelos y desarrollos detallados para Regresión Lineal y Regresión Logística.
