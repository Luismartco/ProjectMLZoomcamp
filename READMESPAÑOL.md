# ProjectMLZoomcamp

El siguiente proyecto es la entrega del Capstone 1 en el Machine Learning Zoomcamp 2024.

## Análisis de Datos para Predicción de Costos
Este proyecto utiliza un modelo de árbol de decisiones para predecir la categorización de costos en función de diferentes variables presentes en un conjunto de datos médicos. El modelo clasifica los costos en tres categorías y evalúa la importancia relativa de las características del conjunto de datos para esta tarea.

## Estructura del Proyecto

1. **Carga y Exploración de Datos**:
   - Se carga un archivo CSV que contiene los datos.
   - Se realiza una exploración inicial para entender las columnas y los tipos de datos.

2. **Preprocesamiento de Datos**:
   - Se eliminan filas con valores faltantes.
   - Las variables categóricas se convierten en variables dummy (codificación one-hot).
   - Se crea una nueva columna `Costo_categorico` para clasificar los costos en tres categorías mediante `pd.qcut`.

3. **División del Conjunto de Datos**:
   - Los datos se dividen en conjuntos de entrenamiento (80%) y prueba (20%).

4. **Entrenamiento del Modelo**:
   - Se utiliza un árbol de decisiones con una profundidad máxima de 5.
   - El modelo se ajusta al conjunto de entrenamiento.

5. **Evaluación del Modelo**:
   - Se calcula la precisión y se genera un reporte de clasificación para el conjunto de prueba.
   - Se muestra la estructura del árbol de decisiones para entender el proceso de toma de decisiones.

6. **Análisis de Importancia de Características**:
   - Se genera un gráfico de las 10 principales características que más influyen en las predicciones del modelo.

## Resultados

### Precisión del Modelo
- El modelo alcanzó una precisión del **40.00%** en el conjunto de prueba.

### Importancia de Características
Las cinco características más importantes para predecir los costos son:

| Característica                  | Importancia |
|---------------------------------|-------------|
| Especialidad_Neurologia         | 0.238697    |
| Especialidad_Neumologia         | 0.224282    |
| Provincia_Los Guandules         | 0.205819    |
| Especialidad_Oftalmologia       | 0.174229    |
| Provincia_Bayahibe              | 0.156972    |

### Visualización de Características
![Gráfico de importancia de características](/media/img.png)

### Estructura del Árbol de Decisiones
Se proporciona una representación textual del árbol para entender las reglas generadas durante el entrenamiento.

```
|--- Especialidad_Neurologia <= 0.50
|   |--- Provincia_Los Guandules <= 0.50
|   |   |--- Especialidad_Neumologia <= 0.50
|   |   |   |--- Provincia_Bayahibe <= 0.50
|   |   |   |   |--- Especialidad_Oftalmologia <= 0.50
|   |   |   |   |   |--- class: 2
|   |   |   |   |--- Especialidad_Oftalmologia >  0.50
|   |   |   |   |   |--- class: 0
|   |   |   |--- Provincia_Bayahibe >  0.50
|   |   |   |   |--- class: 1
|   |   |--- Especialidad_Neumologia >  0.50
|   |   |   |--- class: 2
|   |--- Provincia_Los Guandules >  0.50
|   |   |--- class: 0
|--- Especialidad_Neurologia >  0.50
|   |--- class: 1
```

## Requisitos
- Python 3.x
- Bibliotecas: `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `seaborn`

## Ejecución del Proyecto
1. Asegúrate de tener instaladas las bibliotecas requeridas.
2. Coloca el archivo de datos (`Pacientes.csv`) en el mismo directorio que el script.
3. Ejecuta el script de Python.
4. Observa los resultados y visualizaciones generados.

## Conclusiones
1. Las especialidades médicas y las provincias tienen una gran influencia en la predicción de costos.
2. Aunque la precisión del modelo no es alta, proporciona información valiosa sobre las variables clave.
3. Este análisis puede guiar futuras mejoras en el modelo y la recopilación de datos.