# Análisis Predictivo de Abandono de Clientes (Churn)
### Aplicación de Machine Learning en el marco de la Industria 4.0
 
**Autor:** Santiago Díaz  
**Curso:** Data Science I — Fundamentos para la Ciencia de Datos | Coderhouse (2026)  
**Dataset:** [IBM Telco Customer Churn — Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
 
---
 
## Descripción
 
Proyecto de ciencia de datos orientado a predecir el abandono de clientes (*churn*) en una empresa de telecomunicaciones. A partir de variables demográficas, contractuales y de consumo, se construyeron y compararon modelos de clasificación capaces de identificar clientes con alta probabilidad de abandono, con el objetivo de habilitar estrategias de retención basadas en evidencia.
 
---
 
## Tecnologías utilizadas
 
- **Python** — pandas, NumPy
- **Visualización** — matplotlib, seaborn, missingno
- **Modelado** — scikit-learn (Logistic Regression, Random Forest, GridSearchCV, Pipeline)
- **Entorno** — Google Colab
---
 
## Estructura del repositorio
 
```
analisis-churn-clientes/
│
├── analisis_churn_santiago_diaz.ipynb   ← Notebook principal (EDA, modelado, evaluación)
├── README.md                            ← Este archivo
└── docs/
    └── informe_churn_santiago_diaz.pdf  ← Informe completo del proyecto
```
 
---
 
## Resumen del análisis
 
- **Dataset:** 7.043 registros, 21 variables, desbalance moderado (73.5% No Churn / 26.5% Churn)
- **Modelos evaluados:** Regresión Logística y Random Forest, ambos integrados en un Pipeline de scikit-learn con preprocesamiento estructurado
- **Optimización:** GridSearchCV con validación cruzada estratificada de 5 folds
- **Métrica principal:** ROC-AUC
- **Resultado:** ambos modelos alcanzaron ROC-AUC 0.84 sin evidencia de overfitting (brecha CV vs. test < 0.01)
- **Modelo final seleccionado:** Regresión Logística (Accuracy 81%), por su mayor interpretabilidad ante rendimiento equivalente
---
 
## Principales hallazgos
 
**Hipótesis confirmadas:**
 
- ✅ **H1 — Antigüedad:** los clientes con menor antigüedad concentran la mayor proporción de abandonos. `tenure` resultó la variable con mayor importancia predictiva (~0.14).
- ✅ **H2 — Tipo de contrato:** los contratos mes a mes son el segundo predictor más relevante (~0.10), con diferencias marcadas frente a contratos anuales o bianuales.
- ✅ **H3 — Cargos mensuales:** cargos más elevados se asocian con mayor tendencia al abandono (~0.09).
**Feature engineering:**  
Se construyó la variable `cargo_relativo = MonthlyCharges / (tenure + 1)`, que captura el costo mensual normalizado por tiempo de permanencia. Su correlación con churn resultó superior a la de `MonthlyCharges` de forma aislada.
 
**Recomendación de negocio:**  
Enfocar las estrategias de retención en clientes nuevos con contratos mensuales y cargos elevados, interviniendo durante los primeros meses de la relación. Reducir el umbral de clasificación de 0.5 a 0.3–0.35 aumenta el recall de churn a costa de más falsos positivos, un trade-off favorable dado que el costo de una campaña innecesaria es menor que el costo de perder un cliente sin intervenir.
 
---
 
## Ejecutar el notebook

[![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1aIo2bsxhvTAlVe9Z_uEFcqyOx63f8EZ3?usp=sharing)
 
---
 
## Fuente de datos
 
IBM Sample Dataset — Telco Customer Churn  
🔗 https://www.kaggle.com/datasets/blastchar/telco-customer-churn
