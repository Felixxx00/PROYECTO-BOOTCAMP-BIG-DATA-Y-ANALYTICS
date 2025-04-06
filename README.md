# Conclusiones de la primera exploración:

### 1. Hay que construir un dataset que contenga toda la información disponible en https://opendata.aemet.es/dist/index.html? de la estación meteorológica de Madrid - Reitro (id: 3195) donde se puede descargar datos meteorológicos de 6 en 6 meses. No se pueden descargar los datos de los últimos 3 días, pero si que se puede descargar ciertos campos de https://www.aemet.es/es/eltiempo/observacion/ultimosdatos?k=mad&l=3195&w=2&datos=det&x=&f=tmax

### 2. Tras construir el dataset, se explora qué problema de Data Science se puede plantear.

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
