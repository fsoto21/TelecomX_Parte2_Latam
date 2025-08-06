# TelecomX_Parte2_Latam
Proyecto de análisis y modelado de cancelación de clientes para TelecomX Latam.
# Informe de Clasificación de Cancelación de Clientes

## 1. Objetivo del Proyecto  
El objetivo principal de este análisis fue identificar los factores más influyentes en la cancelación de clientes dentro de una empresa de telecomunicaciones, usando datos históricos de clientes. Se entrenaron varios modelos de clasificación para predecir si un cliente cancelaría el servicio (Churn) y se evaluó el desempeño con métricas relevantes como el F1-score y la matriz de confusión. El fin es apoyar en la toma de decisiones para mejorar la retención de clientes.

## 2. Preparación de los Datos  
Los datos usados ya estaban preprocesados, con las siguientes características:  
- Limpios, sin valores nulos significativos tras imputaciones.  
- Variables categóricas codificadas mediante one-hot encoding.  
- Variables numéricas normalizadas y estandarizadas.  
- La variable objetivo `Churn` binarizada (0 = no canceló, 1 = canceló).

## 3. Modelos Utilizados  
Se entrenaron y compararon los siguientes modelos:  
- **RandomForestClassifier**  
- **XGBoostClassifier**  
- **KNeighborsClassifier (KNN)**  

## 4. Métricas de Evaluación  
Para comparar los modelos se usaron:  
- **F1-score:** Equilibrio entre precisión y recall, especialmente útil en conjuntos con clases desbalanceadas.  
- **Matriz de Confusión:** Para evaluar rendimiento específico en cada clase (clientes que cancelan y que no cancelan).

## 5. Importancia de las Variables  
### 5.1 RandomForestClassifier  
Las variables más influyentes (top 10) fueron:  
- Tenure (tiempo como cliente)  
- Tipo de contrato (mensual, anual, bienal)  
- Cargos mensuales y totales  
- Tipo de servicio de internet (DSL, Fibra óptica, Ninguno)  
- Servicios adicionales como soporte técnico y seguridad online  

### 5.2 XGBoostClassifier  
Variables clave:  
- Cargos totales y mensuales  
- Tenure (tiempo con la empresa)  
- Indicadores de servicios contratados y métodos de pago  

## 6. Resultados de los Modelos  
- **XGBoost** obtuvo el mejor desempeño con un F1-score CV aproximado de 0.82, mostrando gran capacidad para distinguir clientes que cancelan.  
- **RandomForest** mostró buen equilibrio entre precisión y recall, con interpretabilidad clara.  
- **KNN** tuvo menor desempeño (F1 alrededor de 0.57) y menor recall en clientes que cancelan, posiblemente por la alta dimensionalidad y presencia de variables categóricas.  

## 7. Sobre Ajuste (Underfitting / Overfitting)  
No se detectaron problemas evidentes de underfitting o overfitting, ya que la performance fue consistente en conjuntos de entrenamiento y prueba para los mejores modelos (XGBoost y RandomForest), indicando buena capacidad de generalización.

## 8. Factores Principales de Cancelación  
- Clientes con menor tiempo de permanencia (tenure) tienen mayor probabilidad de cancelar.  
- Contratos mensuales incrementan la tasa de cancelación frente a contratos anuales o bianuales.  
- Clientes con cargos mensuales o totales elevados tienen más tendencia a cancelar.  
- El uso de servicios de internet como Fibra óptica se asocia a mayor cancelación.  
- Falta de servicios complementarios (seguridad online, soporte técnico) también impacta negativamente en la retención.

## 9. Estrategias de Retención Recomendadas  
- Promover contratos de largo plazo con incentivos y descuentos.  
- Diseñar paquetes económicos para clientes con altos cargos o segmentación personalizada.  
- Incorporar servicios de soporte y seguridad online como parte del servicio estándar.  
- Implementar campañas de fidelización para clientes nuevos, en especial durante sus primeros meses.  
- Monitorear continuamente los indicadores clave para actuar proactivamente sobre clientes en riesgo.

## 10. Conclusión  
El análisis realizado, junto con el entrenamiento y comparación de modelos, permitió identificar claramente los factores que impactan la cancelación de clientes. XGBoost mostró ser el modelo más robusto para esta tarea, y los insights generados son útiles para diseñar estrategias de retención efectivas. Este enfoque puede integrarse en sistemas de alerta temprana para mitigar la pérdida de clientes mediante intervenciones personalizadas.
