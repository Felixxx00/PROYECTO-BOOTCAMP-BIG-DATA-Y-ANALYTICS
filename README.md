# Conclusiones de la primera exploración:

### 1. Hay que construir un dataset que contenga toda la información disponible en https://opendata.aemet.es/dist/index.html? de la estación meteorológica de Madrid - Reitro (id: 3195) donde se puede descargar datos meteorológicos de 6 en 6 meses. No se pueden descargar los datos de los últimos 3 días, pero si que se puede descargar ciertos campos de https://www.aemet.es/es/eltiempo/observacion/ultimosdatos?k=mad&l=3195&w=2&datos=det&x=&f=tmax

### 2. Se tiene que descargar las estadísticas anuales disponibles (2018 - 2022) de EFMA https://www.aemet.es/es/datos_abiertos/estadisticas/fenomenos_meteorologicos_adversos El 31 de marzo de este mes habrá info nueva

### 3. Se obtiene un reporte de https://sinobas.aemet.es/ que es el Sistema de Notificación de Observaciones Atmosféricas Singulares

### 4. Tras obtener todos los datos tabulares, se unen por la fecha de evento u otro campo verificandose la validez y consistencia del dato. Se analiza lo construido con estadísticas descriptivas y objetos visuales (valorar la posibilidad de hacerlo en Tableau o Power BI) y se construye un modelo de clasificación que indique cuando va a ocurrir un FMA (Fenómeno Meterológico Adverso) o un OAS (Observación Atmosférica Singular). También sería interesante estudiar los datos que reporta esta estación en las fechas próximas a estos fenómenos