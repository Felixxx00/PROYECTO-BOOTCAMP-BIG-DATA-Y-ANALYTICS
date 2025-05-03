# 🌤️ Introducción

Este trabajo tiene como objetivo analizar datos meteorológicos históricos de la estación de **Madrid - Retiro (ID: 3195)**, proporcionados por la API de **AEMET (Agencia Estatal de Meteorología)**. A partir de estos datos, se construye un dataset extenso que permite aplicar técnicas de **análisis de series temporales** para estudiar y predecir el comportamiento del clima en esta región.

Mediante el uso del modelo **AutoARIMA**, se busca realizar predicciones a corto plazo y evaluar la capacidad de ajuste de este tipo de modelos en contextos meteorológicos reales. El proyecto también explora el proceso completo de adquisición, preparación y análisis de datos, sentando las bases para posibles mejoras con modelos más complejos en el futuro.

# ⚙️ Instalación

## Requisitos previos

- **Python 3.x**
- **pip** (gestor de paquetes de Python)

## Configuración del entorno

1. **Clonar el repositorio**:
    ```bash
    git clone https://github.com/Felixxx00/PROYECTO-BOOTCAMP-BIG-DATA-Y-ANALYTICS.git
    cd PROYECTO-BOOTCAMP-BIG-DATA-Y-ANALYTICS
    ```

2. **(Recomendado) Crear y activar un entorno virtual**:

    - **Windows**:
        ```bash
        python -m venv venv
        .\venv\Scripts\activate
        ```

    - **Linux/Mac**:
        ```bash
        python -m venv venv
        source venv/bin/activate
        ```

3. **Instalar las dependencias**:
    ```bash
    pip install -r requirements.txt
    ```

# 📚 API Key y Ejecución de Notebooks

Para que el análisis se ejecute correctamente, es necesario obtener la API KEY en https://opendata.aemet.es/centrodedescargas/altaUsuario y guardarlo en:

    API_KEY_AEMET.txt

Hay que ejecutar los notebooks en el siguiente **orden**:

1. **Notebook 1**: **1. AEMET Exploración y enfoque del análsis a reolver.ipynb**
   - Es sencillamente una **exploración** de la API de la AEMET https://opendata.aemet.es/opendata/sh/b3aa9d28. 

2. **Notebook 2**: **2. AEMET Construccion del dataset a analizar.ipynb**
   - Este notebook se encarga de **obtener los datos** desde la API de AEMET y **generar el dataset** necesario para el análisis.

3. **Notebook 3**: **3. AEMET Preprocesamiento dataset y AutoARIMA.ipynb**
   - Este es el último notebook, donde se diseña el conjunto de entrenamiento y de test tras una limpieza, visualización y tratamiento de los datos y se aplica el modelo **AutoARIMA** para realizar las predicciones y obtener las conclusiones del análisis.

> 🔑 **Nota importante**: Asegúrate de ejecutar los notebooks en este orden, ya que el **Notebook 2** depende de los datos generados por el **Notebook 1**, y el **Notebook 3** depende de los resultados del **Notebook 2**.


# 📊 Descripción del análisis

### 1️⃣ Obtención de datos

- Se obtiene la **API Key** en: [https://opendata.aemet.es/centrodedescargas/altaUsuario](https://opendata.aemet.es/centrodedescargas/altaUsuario)
- Se construye un **dataset** con toda la información disponible sobre la estación meteorológica **Madrid - Retiro (ID: 3195)** desde: [https://opendata.aemet.es/dist/index.html](https://opendata.aemet.es/dist/index.html)
- ⚠️ La API solo permite descargar datos en intervalos máximos de **6 meses**
- ❌ No se pueden descargar los datos de los **últimos 3 días**, aunque sí es posible acceder a ciertos campos recientes desde:
  [https://www.aemet.es/es/eltiempo/observacion/ultimosdatos?k=mad&l=3195&w=2&datos=det&x=&f=tmax](https://www.aemet.es/es/eltiempo/observacion/ultimosdatos?k=mad&l=3195&w=2&datos=det&x=&f=tmax)

---

### 2️⃣ Análisis y modelado

- Una vez construido el dataset, se plantea un problema de **Data Science**
- Se decide realizar un **análisis de series temporales** utilizando el modelo **AutoARIMA**. La variable a predecir es la precipitación acumulada.
- 📆 Para el conjunto de test se usan **30 días**, y para entrenamiento se utilizan **7.059 días** (aproximadamente **19 años y 4 meses**)
- ✅ Al ejecutar los **3 notebooks** en el orden indicado, el dataset se **actualiza automáticamente** conectándose a la API

---

### 3️⃣ Conclusiones

- 📌 El análisis muestra que hay margen de mejora
- Se pueden explorar **otros modelos** que ajusten mejor la serie temporal
- El objetivo es lograr una **predicción meteorológica más precisa y realista** 🔍🌦️


# Descripción del Dataset

# 📊 Servicio del Banco Nacional de Datos Climatológicos. https://opendata.aemet.es/opendata/sh/b3aa9d28

## 📝 Descripción General

- **Unidad generadora:** Servicio del Banco Nacional de Datos Climatológicos  
- **Periodicidad:** Una vez al día, con un retardo de 4 días  
- **Descripción:** Climatologías diarias  
- **Formato de datos:** `application/json`  
- **Copyright:** © AEMET. Autorizado el uso de la información y su reproducción citando a AEMET como autora de la misma.  
- **Nota legal:** [https://www.aemet.es/es/nota_legal](https://www.aemet.es/es/nota_legal)

---

## 📦 Campos de Datos Incluidos

A continuación, se describen los campos incluidos en el conjunto de datos, con sus características:

| Nº | Campo         | Descripción                                                                 | Tipo de dato | Unidad                      | Requerido |
|----|---------------|------------------------------------------------------------------------------|--------------|-----------------------------|-----------|
| 0  | `fecha`       | Fecha del día (formato AAAA-MM-DD)                                          | string       | —                           | ✅         |
| 1  | `indicativo`  | Indicativo climatológico                                                    | string       | —                           | ✅         |
| 2  | `nombre`      | Nombre (ubicación) de la estación                                           | string       | —                           | ✅         |
| 3  | `provincia`   | Provincia de la estación                                                    | string       | —                           | ✅         |
| 4  | `altitud`     | Altitud de la estación sobre el nivel del mar                               | float        | m                           | ✅         |
| 5  | `tmed`        | Temperatura media diaria                                                    | float        | °C                          | ❌         |
| 6  | `prec`        | Precipitación diaria (07 a 07)                                              | float        | mm *(Ip < 0.1 mm, Acum)*    | ❌         |
| 7  | `tmin`        | Temperatura mínima del día                                                  | float        | °C                          | ❌         |
| 8  | `horatmin`    | Hora y minuto de la temperatura mínima                                      | string       | UTC                         | ❌         |
| 9  | `tmax`        | Temperatura máxima del día                                                  | float        | °C                          | ❌         |
| 10 | `horatmax`    | Hora y minuto de la temperatura máxima                                      | string       | UTC                         | ❌         |
| 11 | `dir`         | Dirección de la racha máxima                                                | float        | decenas de grado *(99 = variable, 88 = sin dato)* | ❌         |
| 12 | `velmedia`    | Velocidad media del viento                                                  | float        | m/s                         | ❌         |
| 13 | `racha`       | Racha máxima del viento                                                     | float        | m/s                         | ❌         |
| 14 | `horaracha`   | Hora y minuto de la racha máxima                                            | string       | UTC                         | ❌         |
| 15 | `sol`         | Insolación                                                                  | float        | horas                       | ❌         |
| 16 | `presmax`     | Presión máxima al nivel de referencia de la estación                        | float        | hPa                         | ❌         |
| 17 | `horapresmax` | Hora de la presión máxima (redondeada a la hora más próxima)                | string       | UTC                         | ❌         |
| 18 | `presmin`     | Presión mínima al nivel de referencia de la estación                        | float        | hPa                         | ❌         |
| 19 | `horapresmin` | Hora de la presión mínima (redondeada a la hora más próxima)                | string       | UTC                         | ❌         |
| 20 | `hrmedia`     | Humedad relativa media diaria                                               | float        | %                           | ❌         |
| 21 | `hrmax`       | Humedad relativa máxima diaria                                              | float        | %                           | ❌         |
| 22 | `horahrmax`   | Hora de la humedad relativa máxima diaria                                   | string       | UTC                         | ❌         |
| 23 | `hrmin`       | Humedad relativa mínima diaria                                              | float        | %                           | ❌         |
| 24 | `horahrmin`   | Hora de la humedad relativa mínima diaria                                   | string       | UTC                         | ❌         |