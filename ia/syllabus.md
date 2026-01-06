# Sílabus básico (OPEIA) — Curso introductorio para escolares

Formato: sesiones de 2 horas.

Objetivo general: introducir a estudiantes escolares en programación en Python y las técnicas básicas de Inteligencia Artificial necesarias para competir en OPEIA. El sílabo prioriza práctica guiada, conceptos intuitivos y pequeñas competencias simuladas.

Duración propuesta: 12 sesiones (2 horas cada una) — 24 horas en total.

Sesión 1 — Entorno y Python básico

- Objetivos: instalar entorno, conceptos básicos de Python (tipos, variables, I/O).
- Contenido: instalación de Python, uso de un editor/IDE, `input`/`print`, números, cadenas, booleanos.
- Actividad: resolver problemas sencillos de lectura/escritura (sumas, formato de salida).
- Tarea: 5 ejercicios de práctica en un judge o scripts locales.

Sesión 2 — Control de flujo y colecciones básicas

- Objetivos: manejar condicionales, bucles y listas.
- Contenido: `if/else`, `for`, `while`, listas, indexación, slicing.
- Actividad: contar elementos, transformar arrays, conteos simples.
- Tarea: problemas de conteo y filtros.

Sesión 3 — Funciones, cadenas y depuración

- Objetivos: escribir funciones reusables y depurar errores comunes.
- Contenido: definición de funciones, argumentos, retorno, manejo de strings, excepciones básicas, uso de `assert` y prints para depurar.
- Actividad: implementar funciones para procesar cadenas y pruebas unitarias simples.
- Tarea: ejercicios con funciones y casos borde.

Sesión 4 — Estructuras de datos y complejidad básica

- Objetivos: conocer diccionarios, conjuntos, tuplas y razones de eficiencia.
- Contenido: `dict`, `set`, operaciones comunes, cuándo usar cada estructura, conceptos de complejidad $O(1), O(n), O(n\log n)$.
- Actividad: resolver problemas usando `set` y `dict` (p. ej.conteo de frecuencias, búsqueda de pares que sumen S).
- Tarea: problemas con hashing y conteos.

Sesión 5 — Manejo de datos: NumPy y pandas (introducción)

- Objetivos: manipular datos tabulares y vectores numéricos.
- Contenido: arrays con NumPy, operaciones vectorizadas, DataFrame básicos con pandas (lectura, filtrado, agrupación simple).
- Actividad: limpieza pequeña de un CSV y operaciones estadísticas.
- Tarea: mini-proyecto: preparar dataset pequeño para modelo.

Sesión 6 — Fundamentos de Machine Learning

- Objetivos: entender el flujo ML: datos → modelo → evaluación.
- Contenido: supervisado vs no supervisado, regresión y clasificación, métricas (accuracy, precision, recall, F1, RMSE), división train/test.
- Actividad: ejemplo teórico con dataset pequeño; cálculo manual de métricas.
- Tarea: experimentar con separación train/test en un dataset proporcionado.

Sesión 7 — scikit-learn: primeros modelos y validación

- Objetivos: entrenar modelos básicos y validar resultados.
- Contenido: `sklearn` pipelines, `LogisticRegression`, `DecisionTree`, `KNeighbors`, `train_test_split`, `cross_val_score`.
- Actividad: entrenamiento de un clasificador y evaluación con CV.
- Tarea: mejorar el modelo mediante ajustes simples.

Sesión 8 — Preprocesamiento y feature engineering

- Objetivos: aprender limpieza, codificación y selección de características.
- Contenido: escalado, codificación one-hot, imputación de valores faltantes, extracción de características simples.
- Actividad: preparar features para un modelo de clasificación.
- Tarea: propuesta de features y comparar desempeño.

Sesión 9 — Selección de modelo y ajuste de hiperparámetros

- Objetivos: comparar modelos y ajustar hiperparámetros.
- Contenido: búsqueda en grid (`GridSearchCV`), `RandomizedSearchCV`, métricas apropiadas, evitar overfitting.
- Actividad: práctica de búsqueda de hiperparámetros en un ejemplo.
- Tarea: tunear un modelo y documentar resultados.

Sesión 10 — Introducción a redes neuronales (conceptos) y un framework

- Objetivos: explicar perceptrón, capas, activaciones y entrenar una red simple.
- Contenido: conceptos de NN, pérdida, optimización; ejemplo con `keras` (TensorFlow) o `PyTorch` (según preferencia).
- Actividad: entrenar una red simple para clasificación en toy dataset (MNIST pequeño/unos dígitos sintéticos).
- Tarea: experimentar con arquitectura básica y tasa de aprendizaje.

Sesión 11 — Tópicos aplicados: visión, NLP y RL (introducción)

- Objetivos: mostrar problemas típicos en OPEIA y técnicas básicas.
- Contenido: visión por computadora (clasificación de imágenes), NLP básico (tokenización, bolsa de palabras), introducción a RL (concepto de agente y recompensa).
- Actividad: ejemplo guiado (clasificador de imágenes pequeño) y discusión de enfoques.
- Tarea: lectura breve y ejemplo práctico elegido por el alumno.

Sesión 12 — Estrategia de competencia, ética y simulacro OPEIA

- Objetivos: preparar a los estudiantes para la dinámica de la competencia.
- Contenido: cómo leer enunciados rápido, dividir tiempo, tests rápidos, formato de envíos, buenas prácticas, reproducibilidad, consideraciones éticas en IA.
- Actividad: mini-contest de 60–90 min seguido de revisión y explicación de soluciones.
- Tarea: resumen de aprendizaje y lista de ejercicios para seguir practicando.

Recursos recomendados

- Plataformas: Kaggle (práctica), Codeforces/AtCoder (problemas algorítmicos), Kattis (problemas estructurados).
- Bibliografía y tutoriales: documentación oficial de Python, NumPy, pandas, scikit-learn, tutoriales de TensorFlow/PyTorch, CP-algorithms para fundamentos.
- Herramientas: Google Colab (rápido acceso a GPU), Anaconda o entornos virtuales, Jupyter notebooks.

Notas pedagógicas

- Cada sesión de 2 horas: 60–75 min explicación + 30–45 min práctica guiada.
- Para escolares, priorizar ejemplos visuales, retroalimentación inmediata y ejercicios acotados.
- Ajustar ritmo según el grupo: añadir sesiones prácticas si su nivel es inicial, o avanzar más rápido si tienen experiencia previa.

¿Quieres que adapte el sílabo a un número distinto de sesiones, añada material imprimible por sesión (diapositivas/hojas de ejercicio) o que genere las plantillas de notebooks para las primeras 3 sesiones?
