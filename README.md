# 📊 NovaRetail+ | Análisis Estadístico y Correlacional de Clientes

Este repositorio contiene el análisis exploratorio y estadístico avanzado realizado para la plataforma **NovaRetail+**, enfocado en evaluar los patrones de comportamiento de los usuarios, la retención (*churn*), la efectividad de la pauta publicitaria y la estructura de ingresos.

🔗 **Acceso al repositorio público:** [Project-Sprint-08---NovaRetail-](https://github.com/sofiacorzo34/Project-Sprint-08---NovaRetail-)

---

## 📌 Objetivos del Proyecto

* **Evaluación de patrones de compra e ingresos:** Analizar la relación lineal y monótona entre las transacciones, la publicidad y los ingresos generados.
* **Detección de colinealidad:** Identificar redundancias entre variables numéricas continuas para optimizar futuros modelos predictivos.
* **Medición de impacto de la membresía Premium y Churn:** Evaluar asociaciones con variables binarias y categóricas.
* **Pruebas de independencia categórica:** Determinar la influencia de factores geográficos y tecnológicos en la tasa de abandono (*churn*).

---

## 🔬 Metodología Estadística Aplicada

El análisis se dividió en tres grandes bloques según el tipo de variables involucradas:

### 1. Variables Continuas vs. Continuas (Pearson & Spearman)
Se evaluaron relaciones lineales y de rango entre pares continuos clave:
* `gasto_publicidad_dirigida` vs. `ingreso_anual`
* `compras_mes` vs. `ingreso_anual`
* `nivel_ingreso` vs. `ingreso_anual`

### 2. Variables Binarias vs. Continuas (Correlación Punto-Biserial)
Se aplicó la prueba punto-biserial junto con su respectivo $p$-value para evaluar diferencias significativas entre grupos dicotómicos:
* `miembro_premium` vs. `ingreso_anual`
* `miembro_premium` vs. `compras_mes`
* `abandono` vs. `gasto_publicidad_dirigida`

### 3. Variables Categóricas (V de Cramér & Prueba Chi-Cuadrado)
Se construyeron tablas de contingencia para evaluar la asociación entre variables cualitativas y su significancia estadística ($p$-value):
* `tipo_dispositivo` vs. `region`
* `tipo_dispositivo` vs. `abandono`
* `region` vs. `abandono`

---

## 📈 Hallazgos Clave

* **Riesgo Alto de Colinealidad:** El par `compras_mes` e `ingreso_anual` presentó una correlación extremadamente alta ($r \approx 0.967$), lo que indica una relación lineal directa casi perfecta. Se recomienda no incluir ambas variables de manera simultánea en modelos de regresión.
* **Impacto de la Membresía Premium:** Aunque la correlación punto-biserial entre `miembro_premium` e `ingreso_anual` es modesta en magnitud ($r_{pb} \approx 0.0931$), su valor $p$ ($3.09 \times 10^{-30}$) confirma que los miembros premium generan un ingreso superior estadísticamente significativo.
* **Independencia en Abandono:** La prueba de V de Cramér y la prueba de $\chi^2$ demostraron que ni el `tipo_dispositivo` ni la `region` están estadísticamente asociados a la tasa de `abandono` ($p > 0.05$). La pérdida de clientes ocurre de manera homogénea sin sesgos territoriales o tecnológicos.

---

## 🛠️ Tecnologías y Librerías Utilizadas

* **Lenguaje:** Python 3.x
* **Manipulación de Datos:** `pandas`, `numpy`
* **Cálculo Estadístico:** `scipy.stats` (`chi2_contingency`, `pointbiserialr`)
