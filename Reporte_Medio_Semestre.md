# Proyecto de Medio Semestre - IA

## Curso: Inteligencia Artificial

## Docente: Yudi Guzman Monteza

# Título del proyecto

Predicción de Rendimiento Académico: Predicción de resultados usando Aprendizaje Supervisado.

---
# Grupo 
Grupo 7

# Integrantes del grupo

| Apellidos | Nombres |
|---|---|
| Perez Rojas | Frey Edson |
| Peralta Farfán | Raymond Alain |
| Tafur Ari | Marco Alejandro |
| Barrientos Torres | Jose Paolo |

---
# 1. Introducción

La "Academia Nova" es una institución educativa de alto nivel que, en los últimos ciclos, ha notado una disparidad en el rendimiento final de sus estudiantes. Mientras que un grupo logra calificaciones de excelencia, otro presenta un rendimiento por debajo de lo esperado. Desarrollar una solución basada en Inteligencia Artificial es de suma importancia, ya que permite al comité académico tomar un enfoque proactivo en lugar de reactivo. Un modelo predictivo es capaz de encontrar patrones ocultos en el historial y hábitos del estudiante para prever su calificación, lo que habilita la creación de tutorías personalizadas y estrategias de intervención temprana.

---

# 2. Problema identificado

El problema principal que se desea abordar es la **identificación tardía del bajo rendimiento académico**. 
A menudo, las instituciones solo notan que un alumno tiene problemas cuando reprueba un examen final. Esto genera:
- Dificultad para tomar decisiones oportunas en el seguimiento del estudiante.
- Gestión limitada de los recursos de tutoría (se asignan tutores de forma general en lugar de a quienes más lo necesitan).
- Riesgo de deserción o repitencia por falta de intervención temprana.

---

# 3. Objetivo del proyecto

Diseñar e implementar un sistema de **Aprendizaje Supervisado** que permita **predecir el Índice de Rendimiento (calificación final)** de un estudiante basándose en sus métricas históricas y hábitos de estudio, utilizando un algoritmo de Regresión Lineal Múltiple.

---

# 4. Descripción de la solución propuesta

Nuestra solución consiste en un modelo predictivo continuo.
- **Entradas del sistema:** Se ingresarán 5 factores fundamentales del estudiante: Horas de Estudio, Puntuaciones Previas, Actividades Extracurriculares (Sí/No), Horas de Sueño y Cantidad de Exámenes de Práctica resueltos.
- **Procesamiento:** Un modelo matemático de Regresión Lineal calculará el peso de cada variable de entrada y generará una ecuación para estimar el rendimiento. Previamente, los datos pasarán por un preprocesamiento numérico (Label Encoding) para las variables categóricas.
- **Salida esperada:** Un valor numérico continuo (del 10 al 100) que representa el *Performance Index* pronosticado para ese alumno.
- **Comportamiento del modelo:** El modelo actuará como una función evaluadora altamente transparente. No será una "caja negra"; proporcionará explícitamente cuánto impacta cada hora extra de estudio o de sueño en la nota final.

---

# 5. Técnicas o algoritmos utilizados

Para este proyecto hemos utilizado la técnica de:
- **Aprendizaje Supervisado:** Específicamente el algoritmo de **Regresión Lineal Múltiple**.
Se seleccionó este algoritmo en lugar de modelos de clasificación (como Árboles de Decisión o KNN) porque nuestro objetivo es predecir un valor numérico continuo (una nota). Además, la Regresión Lineal destaca por su alta interpretabilidad, permitiendo a la academia explicar fácilmente las razones de una predicción a los estudiantes y padres de familia.

---

# 6. Dataset o datos utilizados

Los datos provienen de un **Dataset público** extraído de la plataforma Kaggle (*Student Performance Multiple Linear Regression*).

- **Cantidad aproximada de registros:** 10,000 registros de estudiantes simulados.
- **Variables principales (Features):**
  1. `Hours Studied` (Horas Estudiadas)
  2. `Previous Scores` (Puntuaciones Previas)
  3. `Extracurricular Activities` (Actividades Extracurriculares) - Variable binaria categórica.
  4. `Sleep Hours` (Horas de Sueño)
  5. `Sample Question Papers Practiced` (Exámenes de práctica)
- **Variable Objetivo (Target):** `Performance Index` (Índice de Rendimiento).

---

# 7. Diseño general del proyecto

El flujo de trabajo se ha programado de forma secuencial en un entorno de Jupyter Notebook:

1. **Carga de datos:** Integración automatizada mediante la API `kagglehub` y uso de DataFrames en Pandas.
2. **Análisis Exploratorio de Datos (EDA):** Generación de histogramas para visualizar la distribución de los estudiantes y matrices de calor (Heatmaps) para medir la correlación entre variables.
3. **Preprocesamiento:** Aplicación de `LabelEncoder` a la variable "Actividades Extracurriculares" para convertirla de Sí/No a valores binarios numéricos (1/0) y evitar la trampa de multicolinealidad.
4. **Entrenamiento:** División del dataset (80% entrenamiento, 20% prueba) y aplicación del algoritmo `LinearRegression` de Scikit-Learn para obtener los coeficientes (pesos).
5. **Evaluación:** Medición de la precisión utilizando métricas como el Coeficiente de Determinación ($R^2$) y el Error Cuadrático Medio (MSE), además del trazado gráfico del Análisis de Residuos (Errores reales vs predichos).

---

# 8. Resultados esperados

Mediante el entrenamiento de este modelo se espera obtener:
- **Predicción de calificaciones altamente precisas:** Un modelo con un $R^2$ superior al 95%, lo que significa que la inmensa mayoría de la nota de un alumno puede ser explicada por estas 5 variables.
- **Medición de Impacto Real (La Ecuación):** La extracción de la ecuación matemática subyacente que revele explícitamente descubrimientos como: "Por cada hora extra de estudio, el índice aumenta en *N* puntos".
- **Mejora en Decisiones Académicas:** Un soporte basado en datos para que los tutores recomienden de manera certera cuántas horas dormir o estudiar para llegar a una nota objetivo.

---

# 9. Herramientas utilizadas

- Lenguaje **Python**
- **Jupyter Notebook** (Entorno de desarrollo)
- **scikit-learn** (Modelado de Regresión Lineal, Métricas, LabelEncoder)
- **pandas** (Manipulación y carga del dataset)
- **matplotlib** y **seaborn** (Generación de gráficos de dispersión, histogramas y heatmaps)
- **kagglehub** (Descarga automática del dataset)

---

# 10. Consideraciones finales

- **Utilidad del proyecto:** La implementación de esta IA permite que cualquier institución educativa pase de un modelo de gestión reactivo (actuar cuando el alumno ya reprobó) a uno completamente predictivo, ahorrando recursos y mejorando la tasa de éxito estudiantil.
- **Posibles limitaciones:** El modelo es lineal, por lo que asume que el progreso es constante. Además, existen variables psicosociales (estado de ánimo, problemas familiares, economía) que no están siendo medidas en este dataset y que indudablemente afectan el rendimiento (el margen de error del modelo).
- **Trabajos futuros:** Integrar variables cualitativas mediante encuestas psicológicas, y probar algoritmos que capturen relaciones no lineales (como Redes Neuronales Regresoras) para comparar su desempeño frente a la regresión lineal.

---

# 11. Referencias

- Russell, S. & Norvig, P. (2021). *Inteligencia Artificial: Un enfoque moderno*.
- Documentación oficial de Scikit-learn (Módulo: `sklearn.linear_model.LinearRegression`).
- Dataset utilizado: *Student Performance (Multiple Linear Regression)* por Nikhil (Kaggle).
- API Oficial de visualización de datos: *Seaborn Data Visualization Library*.
