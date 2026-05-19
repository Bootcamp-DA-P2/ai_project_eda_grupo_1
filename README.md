# ai_project_eda_grupo_1
Proyecto de Análisis Exploratorio de Datos (EDA) centrado en la limpieza, procesamiento y visualización de datos para extraer insights relevantes y facilitar la toma de decisiones basada en datos.

# 🦠 Análisis Exploratorio de Datos — COVID-19 en EE.UU.

> Proyecto de EDA realizado sobre datos históricos de la pandemia de COVID-19 en Estados Unidos, con el objetivo de presentar conclusiones limpias y accionables al equipo directivo.

---

## 📋 Descripción

Este proyecto realiza un **Análisis Exploratorio de Datos (EDA)** completo sobre el dataset histórico del [COVID Tracking Project](https://covidtracking.com/data/download), que registró datos diarios sobre la pandemia en Estados Unidos desde 2020 hasta marzo de 2021.

El objetivo es transformar datos crudos en información significativa: limpiar, explorar, procesar, visualizar y extraer conclusiones que cuenten la historia de cómo evolucionó la pandemia en EE.UU.

---

## 📁 Estructura del Repositorio

```
📦 ia_project_eda_grupo1
 ┣ 📓 EDA-exploration-data-analyst.ipynb        # Notebook principal con el análisis completo
 ┣ 📄 .gitignore
 ┗ 📄 README.md
```
---

## 🗂️ Dataset

- **Fuente:** [The COVID Tracking Project](https://covidtracking.com/data/download)
- **Archivo:** `national-history.csv`
- **Cobertura:** Datos nacionales diarios de EE.UU. — enero 2020 a marzo 2021
- **Registros:** ~400 filas / 40+ columnas

### Columnas principales utilizadas

| Columna | Descripción |
|---|---|
| `date` | Fecha del registro |
| `states` | Número de estados que reportaron ese día |
| `positive` | Casos positivos acumulados |
| `positiveIncrease` | Nuevos casos diarios |
| `death` | Muertes acumuladas |
| `deathIncrease` | Nuevas muertes diarias |
| `hospitalizedCurrently` | Hospitalizados activos |
| `inIcuCurrently` | Pacientes en UCI activos |
| `onVentilatorCurrently` | Pacientes en ventilador activos |
| `totalTestResults` | Total de pruebas realizadas |
| `totalTestResultsIncrease` | Nuevas pruebas diarias |

---

## 🔍 Análisis Realizado

### 1. Carga y exploración inicial
- Inspección de tipos de dato con `dtypes` y `info()`
- Identificación de columnas numéricas, categóricas y temporales
- Conversión de `date` a `datetime` y variables numéricas a `Int64`

### 2. Limpieza de datos
- Detección y tratamiento de valores nulos con `isnull()` y `fillna(0)`
- Identificación de filas duplicadas con `duplicated()`
- Verificación de fechas repetidas

### 3. Estadística descriptiva
- `describe()` para resumen estadístico general
- Análisis de asimetría (`skew`) y curtosis (`kurt`) por variable

### 4. Detección de outliers
- Visualización con boxplots (Seaborn)
- Método IQR (rango intercuartílico) para límites superior e inferior
- Identificación de días atípicos en `positiveIncrease` y `deathIncrease`

### 5. Visualizaciones
- Histogramas con KDE para distribución de variables clave
- Gráficos de línea para evolución temporal
- Scatter plots para relaciones entre variables
- Boxplots y violin plots
- Heatmap de correlaciones (Pearson)

### 6. Análisis de correlaciones
- Correlación de Pearson y Spearman entre `positiveIncrease` y `deathIncrease`
- Heatmap de correlaciones entre métricas COVID
- Análisis de lag temporal (desfase de ~14 días entre casos y muertes)

---

## 🛠️ Tecnologías

| Librería | Uso |
|---|---|
| `requests` | Consumo de API y descarga de datos |
| `pandas` | Manipulación y análisis de datos |
| `matplotlib` | Gráficos estáticos base |
| `seaborn` | Visualizaciones estadísticas |
| `bokeh` | Gráficos interactivos |
| `scipy.stats` | Correlaciones estadísticas (Pearson, Spearman) |

---

## 🚀 Cómo ejecutar

1. Clona el repositorio:
```bash
git clone https://github.com/tu-usuario/eda-covid19.git
cd ai_project_eda_grupo_1.git
```

2. Instala las dependencias:
```bash
pip install pandas matplotlib seaborn bokeh scipy requests
```

3. Descarga el dataset:
```bash
# Descarga manual desde
# https://covidtracking.com/data/download/national-history.csv
```

4. Abre el notebook en Google Colab:
```bash
- Ve a Google Colab
- Selecciona Archivo → Abrir notebook → GitHub
- Busca el repositorio y abre EDA-exploration-data-analyst.ipynb
- Sube el archivo national-history.csv al entorno de Colab
- Ejecuta las celdas en orden

```

---

## 📊 Principales Hallazgos

- Los **nuevos casos diarios** presentan distribución fuertemente asimétrica a la derecha, con picos en enero 2021 coincidiendo con las fiestas navideñas.
- Las **muertes diarias** siguen a los casos con un desfase aproximado de **14 días**, confirmado con análisis de correlación con lag.
- Existe una **correlación muy alta** entre `hospitalizedCurrently` e `inIcuCurrently` (~0.9+), ya que UCI es subconjunto de hospitalizados.
- Se detectaron **28 días atípicos** en `deathIncrease`, con el pico máximo el 12 de febrero de 2021 (5.427 muertes en un día).
- La **tasa de positividad** (`positiveIncrease / totalTestResultsIncrease`) permite medir la presión sobre el sistema de salud de forma más precisa que los casos absolutos.

---

## 👥 Equipo

> Ana Paula Montiel
> Noelia Sánchez
> Romina Navea 

---

## 📄 Licencia

Los datos utilizados están bajo licencia [CC BY 4.0](https://covidtracking.com/license) del COVID Tracking Project / The Atlantic.
