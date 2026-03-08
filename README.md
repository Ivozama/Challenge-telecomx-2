# Telecom X - Predicción de Cancelación de Clientes (Churn) – Parte 2

## Descripción del Proyecto

Este proyecto tiene como objetivo analizar los factores que influyen en la cancelación de clientes (churn) en la empresa ficticia **Telecom X** y construir modelos predictivos capaces de anticipar qué clientes tienen mayor probabilidad de abandonar el servicio.

A través de técnicas de **análisis de datos y machine learning**, se busca identificar patrones en el comportamiento de los clientes y proporcionar información que permita desarrollar estrategias de **retención más efectivas**.

El análisis se basa en un conjunto de datos previamente procesado en la **Parte 1 del proyecto (ETL)**, donde se realizó la limpieza, transformación y preparación inicial de los datos.

---

# Objetivo del Análisis

El objetivo principal del proyecto es **predecir la cancelación de clientes** utilizando variables relevantes relacionadas con el perfil del cliente, su permanencia en la empresa y su comportamiento de consumo.

Específicamente se busca:

* Identificar los factores que más influyen en la cancelación de clientes.
* Construir modelos predictivos que permitan anticipar el churn.
* Evaluar el desempeño de distintos modelos de machine learning.
* Proponer estrategias de retención basadas en los resultados obtenidos.

---

# Estructura del Proyecto

El proyecto se organiza de la siguiente manera:

```
TelecomX-Churn-Prediction/
│
├── TelecomX_Modelado.ipynb
│   Notebook principal con el análisis exploratorio,
│   modelado predictivo y conclusiones.
│
├── datos_tratados.csv
│   Dataset limpio y preparado durante la etapa ETL
│   utilizado para el modelado.
│
├── README.md
│   Documentación del proyecto.
│
└── visualizaciones/
    Carpeta opcional con gráficos generados durante el análisis.
```

---

# Preparación de los Datos

Antes de entrenar los modelos predictivos se realizaron varias etapas de preparación de datos.

## Clasificación de variables

Las variables del dataset fueron clasificadas en dos tipos principales:

**Variables numéricas**

* Tenure (tiempo de permanencia del cliente)
* Charges.Monthly (cargo mensual)
* Charges.Total (gasto total)
* Cuentas_Diarias
* SeniorCitizen

**Variables categóricas**

* Género
* Tipo de contrato
* Método de pago
* Servicios adicionales contratados
* Facturación electrónica
* Dependientes y pareja

---

## Codificación de variables categóricas

Las variables categóricas fueron transformadas a formato numérico utilizando **One-Hot Encoding** con la función:

```
pd.get_dummies()
```

Esto permite que los algoritmos de machine learning puedan procesar correctamente la información.

---

## Manejo de valores faltantes

Durante el proceso de modelado se detectaron valores faltantes (NaN) en algunas variables. Para evitar errores en los algoritmos de machine learning, estos valores fueron reemplazados utilizando **la media de cada columna numérica**.

Esta estrategia permite mantener la distribución general de los datos sin eliminar observaciones.

---

## División de los datos

Para evaluar el rendimiento de los modelos, el dataset fue dividido en:

* **80% datos de entrenamiento**
* **20% datos de prueba**

Esto permite entrenar los modelos con una parte de los datos y evaluar su capacidad de generalización en datos no vistos.

---

## Normalización de variables

Algunos algoritmos de machine learning son sensibles a la escala de los datos.

Por esta razón se aplicó **normalización utilizando StandardScaler** en el modelo de **Regresión Logística**.

La normalización transforma las variables para que tengan:

* media = 0
* desviación estándar = 1

Esto mejora la estabilidad y el rendimiento del modelo.

---

# Modelos Utilizados

Se entrenaron dos modelos de machine learning para predecir la cancelación de clientes.

## Regresión Logística

La regresión logística es un modelo estadístico utilizado para problemas de clasificación binaria. En este caso se utilizó para predecir si un cliente cancelará o no el servicio.

Este modelo requiere normalización de los datos para garantizar un correcto cálculo de los coeficientes.

---

## Random Forest

Random Forest es un algoritmo basado en **múltiples árboles de decisión**, que combina los resultados de varios árboles para mejorar la precisión de las predicciones.

Este modelo no requiere normalización de los datos y es especialmente útil para detectar relaciones complejas entre variables.

---

# Análisis Exploratorio de Datos (EDA)

Durante el análisis exploratorio se realizaron diferentes visualizaciones para comprender mejor el comportamiento de los clientes.

Entre los principales análisis se incluyen:

* Distribución de clientes que cancelaron frente a los que permanecen activos.
* Matriz de correlación entre las variables del dataset.
* Análisis de la relación entre **tiempo de permanencia (tenure)** y cancelación.
* Relación entre **gasto total y cancelación**.
* Visualización de la importancia de variables en el modelo Random Forest.

Estos análisis permitieron identificar patrones importantes asociados al churn.

---

# Principales Insights

A partir del análisis realizado se identificaron varios factores que influyen significativamente en la cancelación de clientes:

* Los clientes con **menor tiempo de permanencia** presentan mayor probabilidad de cancelar el servicio.
* Los **contratos de corto plazo** están asociados con mayores tasas de cancelación.
* El nivel de **gasto mensual y gasto total** también influye en la probabilidad de churn.
* Algunas combinaciones de servicios contratados pueden aumentar o reducir la probabilidad de cancelación.

---

# Cómo Ejecutar el Proyecto

Para ejecutar el análisis se recomienda utilizar **Python 3 y Jupyter Notebook o Google Colab**.

## 1. Instalar las bibliotecas necesarias

```
pip install pandas
pip install numpy
pip install matplotlib
pip install seaborn
pip install scikit-learn
```

## 2. Abrir el notebook

Abrir el archivo:

```
TelecomX_Modelado.ipynb
```

## 3. Cargar los datos

Asegurarse de que el archivo:

```
datos_tratados.csv
```

se encuentre en el mismo directorio que el notebook.

Luego ejecutar todas las celdas del cuaderno para reproducir el análisis completo.

---

# Conclusión

El uso de técnicas de análisis de datos y modelos de machine learning permitió identificar patrones relevantes asociados a la cancelación de clientes en Telecom X.

Entre los factores más influyentes se encuentran el tiempo de permanencia del cliente, el tipo de contrato y el comportamiento de gasto. Los resultados obtenidos demuestran que modelos como **Random Forest** pueden ser altamente efectivos para predecir el churn.

Este tipo de análisis puede ayudar a las empresas a desarrollar estrategias de retención más efectivas y mejorar la relación con sus clientes.

---

# Autor: Ivan Zamaniego

Proyecto desarrollado como parte del desafío de análisis de datos y machine learning en **Telecom X – Parte 2**.
