# Proyecto: Predicción de Evasión de Clientes (Churn) - Telecom X

## Descripción del Proyecto
En este proyecto, asumí el rol de un **Analista de Machine Learning** para enfrentar uno de los mayores desafíos de la empresa "Telecom X": la pérdida de clientes. Mi objetivo fue construir un pipeline de datos capaz de predecir qué clientes tienen mayor probabilidad de cancelar su servicio, permitiendo que el equipo de marketing actúe de manera proactiva.

---

## Paso a Paso del Desarrollo

### 1. Limpieza y Curación de Datos
Inicié el proceso explorando el dataset original. Mi primera misión fue asegurar la calidad de la información:
* **Gestión de Nulos:** Identifiqué y eliminé valores nulos en columnas críticas como `Facturacion_Total` y en la etiqueta objetivo `Evasion`.
* **Depuración de Variables:** Eliminé columnas irrelevantes para el aprendizaje, como `ID_Cliente`, y detecté redundancias matemáticas (multicolinealidad) eliminando la columna `Cuentas_Diarias`.

### 2. Ingeniería de Características (Preprocessing)
Para que los modelos pudieran "entender" los datos, realicé las siguientes transformaciones:
* **Codificación:** Utilicé **One-Hot Encoding** (con `drop_first=True`) para convertir variables categóricas como el tipo de internet o contrato en variables numéricas.
* **Estandarización:** Apliqué un **StandardScaler** para llevar variables de distintas magnitudes (como el gasto mensual vs. los meses de contrato) a una escala común con media 0 y desviación estándar 1.



### 3. Balanceo de Clases (SMOTE)
Al analizar la proporción de clientes, noté un desbalance (más clientes permanecen de los que se van). Para evitar que el modelo se volviera "perezoso", utilicé **SMOTE** para generar ejemplos sintéticos de la clase minoritaria (clientes que cancelan), equilibrando así el entrenamiento.

### 4. Modelado y Entrenamiento
Entrené y comparé dos arquitecturas diferentes para evaluar cuál se adaptaba mejor al problema:
1. **Regresión Logística:** Como modelo base, ideal por su interpretabilidad.
2. **Random Forest:** Un modelo de ensamble potente para capturar relaciones no lineales entre las variables.



### 5. Evaluación y Análisis Crítico
Evalué ambos modelos usando matrices de confusión y métricas clave (**Precision, Recall, F1-Score**). 
* Determinamos que el **Recall** es nuestra métrica más importante, ya que preferimos identificar a un cliente que podría irse (aunque sea un falso positivo) que perder a uno por no haberlo detectado.

### 6. Interpretación de Resultados
Finalmente, analicé la **Importancia de las
