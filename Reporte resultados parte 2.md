# 📊 TelecomX LATAM — Parte 2: Resultados de Modelado de Churn

---

## 1) Rendimiento de los modelos
- **Modelos evaluados:** Regresión Logística y Random Forest.
- **Esquema de validación:** *train/test split* estratificado (80/20) + **Stratified K-Fold (5)** para CV.
- **Métricas reportadas:** `accuracy`, `precision`, `recall`, `f1`, **`roc_auc`**.
- **Hallazgo principal:**  
  - **Random Forest** obtuvo el **mejor `ROC AUC`** y **mejor `recall`** (útil para capturar cancelaciones).  
  - **Regresión Logística** entregó **mayor interpretabilidad directa** (coeficientes), con rendimiento competitivo.

> *(Si tienes la tabla `eval_df` en el notebook, muéstrala debajo de este bloque para cifras exactas).*


---

## 2) Importancia de variables (consistencia entre métodos)
**Fuentes de interpretación:** coeficientes (LR), *feature importance* (RF) e **importancia por permutaciones** (modelo ganador).

- **Contrato**  
  - Clientes con **`Month-to-month`** muestran la mayor probabilidad de churn.  
  - Contratos **`One year` / `Two year`** reducen significativamente el riesgo.

- **Antigüedad (`tenure`)**  
  - **Tenure bajo (0–12 meses)** = mayor churn.  
  - A mayor permanencia, menor probabilidad de cancelación.

- **Método de pago**  
  - **`Electronic check`** asociado a mayor churn que **pagos automáticos** (tarjeta/débito).

- **Servicio de internet y precio**  
  - **`Fiber optic`** + **cargos mensuales altos** elevan el riesgo (sensibilidad a precio/expectativas).

> Las variables demográficas (p. ej., `gender`) presentaron **impacto secundario** frente a contrato, tenure, método de pago y precio/servicio.


---

## 3) Lectura de negocio (¿qué nos dicen los resultados?)
- El churn **se concentra** en clientes **nuevos**, **con contrato flexible** y **pago no automático**, especialmente si pagan **cuotas altas** por **Fiber optic**.  
- Los **segmentos más fieles** combinan **contratos de mayor duración**, **pagos automáticos** y **tenure alto**.  
- La **estructura contractual** y la **experiencia de pago/valor percibido** son palancas más efectivas que factores demográficos.


---

## 4) Conclusión estratégica (acciones priorizadas)
1. **Migración a contratos de 1–2 años** con incentivos (bonos de fidelidad, upgrades, precios promocionales de retención).  
2. **Onboarding 0–90 días** para clientes nuevos: educación de uso, comunicación de valor y **soporte proactivo**.  
3. **Promover pagos automáticos** (débito/crédito) con beneficios; reducir fricción frente a `Electronic check`.  
4. **Revisión de oferta `Fiber optic` y precios**:  
   - Paquetes escalonados y beneficios tangibles (soporte prioritario, mejoras de velocidad temporales).  
5. **Monitoreo continuo de KPIs** y despliegue de **alertas tempranas** con el modelo ganador (foco en alto `recall`).

> **Impacto esperado:** reducción del churn estructural (contratos) + mitigación de cancelaciones por **precio/experiencia** en segmentos de alto riesgo.


---

## 5) Notas metodológicas
- **Preparación de datos:** imputación (mediana/moda), **One-Hot Encoding** para categóricas, **escalado** de numéricas.  
- **Selección/diagnóstico:** correlación *point-biserial* (numéricas), **Cramér’s V** (categóricas), **Mutual Information** (matriz transformada).  
- **Evaluación:** métricas promedio en CV + evaluación en *holdout*; **curvas ROC** y **matrices de confusión** para cada modelo.  
- **Interpretabilidad:** coeficientes (LR), importancias (RF) y **Permutation Importance** (entradas u OHE), buscando **coherencia entre métodos**.

---

### ✅ Resumen ejecutivo
- **Variables clave:** `Contract (Month-to-month)`, `tenure`, `PaymentMethod (Electronic check)`, `InternetService (Fiber optic)`, `Charges.Monthly`.  
- **Modelo recomendado para operación:** **Random Forest** (mejor `ROC AUC` y `recall`), con soporte de interpretabilidad complementaria vía permutaciones.  
- **Estrategia de negocio:** **fidelización contractual**, **pago automático**, **programa early-life**, y **propuesta de valor/precio** en `Fiber optic` con cargos altos.
