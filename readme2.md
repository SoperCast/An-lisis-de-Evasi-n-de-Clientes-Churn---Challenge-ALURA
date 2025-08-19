
---

## 🛠️ Tecnologías utilizadas
- **Python** (pandas, numpy, matplotlib, seaborn, scikit-learn)  
- **Jupyter Notebook**  
- **Análisis Exploratorio de Datos (EDA)**  
- **Modelado supervisado (clasificación)**  
- **Interpretabilidad de modelos**

---

## 📊 Metodología
1. **Preparación de datos**  
   - Limpieza y tipificación de variables.  
   - Codificación de categóricas con OneHotEncoder.  
   - Escalado de numéricas con StandardScaler.  
   - Imputación de valores nulos.  

2. **Selección de variables**  
   - Correlación *point-biserial* para numéricas.  
   - Cramér’s V para categóricas.  
   - Mutual Information sobre variables transformadas.  

3. **Entrenamiento de modelos**  
   - **Logistic Regression** (coeficientes interpretables).  
   - **Random Forest** (robustez, mejor capacidad predictiva).  

4. **Evaluación y métricas**  
   - Validación cruzada (StratifiedKFold).  
   - Evaluación en *holdout*.  
   - Reportes de clasificación, matrices de confusión y curvas ROC.  

5. **Interpretabilidad**  
   - Coeficientes de regresión.  
   - Importancias del Random Forest.  
   - **Permutation Importance** para robustecer la lectura.

---

## 📈 Principales resultados
- **Random Forest** fue el mejor modelo (mayor `ROC AUC` y `recall`).  
- **Factores clave asociados al churn:**
  - Contratos **Month-to-month** con alta propensión a abandono.  
  - **Tenure bajo (0–12 meses)** como periodo crítico.  
  - **Método de pago: Electronic check** asociado a mayor churn.  
  - Clientes con **Fiber optic** y **cargos mensuales altos** muestran mayor sensibilidad.  

---

## 📢 Conclusión estratégica
1. **Migrar a contratos de 1–2 años** con incentivos para reducir churn estructural.  
2. **Onboarding proactivo en los primeros 90 días** (soporte, educación y comunicación de valor).  
3. **Promover pagos automáticos** (tarjeta/débito) con beneficios, reduciendo la fricción de `Electronic check`.  
4. **Optimizar la propuesta de valor en Fiber optic**, ajustando precio o reforzando beneficios percibidos.  
5. **Monitorear churn en tiempo real** con el modelo entrenado, aplicando alertas tempranas sobre clientes de alto riesgo.  

---

## ✅ Resumen
Este proyecto entrega un **pipeline reproducible de modelado de churn**, combinando análisis exploratorio, selección de variables, entrenamiento de modelos supervisados y conclusiones estratégicas.  
El resultado final es una **herramienta analítica práctica** para apoyar la **retención de clientes** en empresas de telecomunicaciones.

---
