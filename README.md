# M-S1-AP1-Prediccion-nacimientos-machine-learning

**Actividad 5 — Maestría en Inteligencia Artificial · Universidad de la Salle**

Predicción del número de nacimientos en Colombia por departamento para el año 2024, utilizando técnicas de Machine Learning y modelos de series temporales sobre datos históricos del DANE (2020–2023).

---

## Descripción

El proyecto construye un modelo predictivo que, a partir de variables geográficas, temporales y sociodemográficas, estima el número mensual de nacimientos por departamento, apoyando la planificación en salud pública.

**Dataset:** Registros de nacimientos del DANE para los años 2020–2023 — más de **2.3 millones de registros** procesados, consolidados en un dataset de **1,584 observaciones** (33 departamentos × 12 meses × 4 años).

---

## Estructura del repositorio

```
├── data/
│   ├── nac2020.csv
│   ├── nac2021.csv
│   ├── nac2022.csv
│   └── nac2023.csv
├── notebook/
│   └── Prediccion_nacimientos_ML.ipynb
├── requirements.txt
└── README.md
```

---

## Metodología

El notebook sigue ocho secciones:

| Sección | Descripción |
|---|---|
| **A. Introducción** | Contexto, objetivo y librerías utilizadas |
| **B. Preprocesamiento** | Cargue, concatenación, eliminación de duplicados y tratamiento de nulos |
| **C. Exploración** | Análisis exploratorio con visualizaciones interactivas (tendencias, estacionalidad, distribución por departamento) |
| **D. Selección del Modelo** | Comparación de cuatro algoritmos: Regresión Lineal, Random Forest, KNN y ARIMA(1,1,1) |
| **E. Entrenamiento** | Entrenamiento del modelo seleccionado (ARIMA) con parámetros (p=1, d=1, q=1) por departamento |
| **F. Evaluación** | Métricas de desempeño sobre holdout temporal estricto (2023 completo) |
| **G. Visualización** | Proyecciones 2024 por departamento, tendencia histórica y totales nacionales |
| **H. Conclusiones** | Interpretación de resultados y limitaciones del modelo |

---

## Modelos comparados

| Modelo | Tipo | R² | MAE | MAPE |
|---|---|---|---|---|
| **ARIMA(1,1,1)** ✅ | Serie temporal | 0.9588 | 187.2 | 18.40% |
| Random Forest | Ensemble (200 árboles) | 0.9811* | 86.9* | 7.65%* |
| KNN (k=10) | Basado en instancias | 0.6241* | 548.2* | 151.86%* |
| Regresión Lineal | Paramétrico lineal | 0.3510* | 794.2* | 187.66%* |

\* *Evaluados con split aleatorio 80/20 (mezcla de años). ARIMA evaluado en holdout temporal estricto: entrenado en 2020–2022, evaluado en 2023 completo (396 observaciones).*

**ARIMA(1,1,1)** fue seleccionado como modelo final por modelar explícitamente la dinámica temporal de cada departamento y producir proyecciones coherentes con la tendencia demográfica observada.

---

## Resultados

- **Total nacional proyectado 2024:** 496,288 nacimientos
- **Tendencia:** reducción sostenida desde 617,681 (2020) hasta 2024, consistente con la transición demográfica colombiana
- **Top 5 departamentos:** Bogotá D.C., Antioquia, Valle del Cauca, Atlántico y Bolívar

---

## Tecnologías

| Librería | Versión | Uso |
|---|---|---|
| `pandas` | — | Manipulación y limpieza de datos |
| `numpy` | — | Operaciones numéricas |
| `scikit-learn` | — | Modelos ML (LR, RF, KNN), métricas y escalado |
| `statsmodels` | — | Modelo ARIMA |
| `plotly` | — | Visualizaciones interactivas |

Instalar dependencias:

```bash
pip install -r requirements.txt
```
