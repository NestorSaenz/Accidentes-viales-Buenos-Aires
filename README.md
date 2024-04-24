![Pandas](https://img.shields.io/badge/-Pandas-333333?style=flat&logo=pandas)
![Numpy](https://img.shields.io/badge/-Numpy-333333?style=flat&logo=numpy)
![Matplotlib](https://img.shields.io/badge/-Matplotlib-333333?style=flat&logo=matplotlib)
![Power BI](https://img.shields.io/badge/-Power%20BI-333333?style=flat&logo=powerbi&logoColor=white)

# Analísis de accidentalidad en Buenos Aires Argentina

Este proyecto simula el rol de un ***Data Analyst*** para el `Observatorio de Movilidad y Seguridad Vial` (OMSV) centro de estudios que se encuentra bajo la órbita de la ***Secretaría de Transporte*** del Gobierno de la Ciudad Autónoma de Buenos Aires, Para ello, se cuenta con un dataset sobre homicidios en siniestros viales durante el period 2016-2021 acaecidos en la Ciudad de Buenos Aires durante el periodo 2016-2021. se puede descargar de la siguiente página Web [Buenos Aires Data](https://data.buenosaires.gob.ar/dataset/victimas-siniestros-viales)

## Objetivo

El objetivo es hacer un análisis de los datos disponibles incluyendo KPIs, con el fin de generar información que le permita a las autoridades tomar medidas de prevención y disminuir la tasa de accidentes fatales que actualmente es de `11 personas por día`.

## Contexto

La muerte por accidentes de tránsito es la primera causa de muerte violenta en el pais, es mas probable morir de un siniestro vial que por un acto delictivo, de ahi la importancia de generar medidas de prevención

## Elaboración del proyecto

La data se extrae de dos archivos formato xlsx:  

*  **HECHOS.xlsx*   Información relacionada con la data física del accidente. Por ejemplo: la fecha, lugar del hecho, tipo de vehículos involucrados, latitud y longitud, acusado del hecho entre otras.

*  **VICTIMAS.xlsx*   Información relacionada con la víctima. Por ejemplo: sexo, edad, rol de la víctima y fecha de fallecimiento.

## ETL (extracción, transformación y carga)

Se extrae la información con pandas y se empieza la transformación, en este notebook se hace un merged con los dos datasets previamente cargados y se comienzan las transformaciones: normalización de columnas, verificación de los tipos de datos, algunos datos por ejemplo de franja horaria donde no hay datos se sustituyen por la moda del conjunto de datos, para visualizar el ETL hacer clic en [ETL](ETL.ipynb)

## EDA (Análisis exploratorio de los datos)

La exploracion de los datos comienza con un análisis descriptivo, donde se visualiza métricas estadísticas como, la media, desviación estándar y distribución por percentiles de los datos, el análisis se basa en tres pilares:

### 1. Análisis por victima

En este paso se exploran caracteristicas de las victimas que pueden influir o están relacionadas con el riesgo de tener un accidente fatal como la edad y género, gráficamente se visualiza que el género masculino tiene un 76% de probabilidad de morir en carretera con un rango etario de [25-41] años.


### 2. Análisis temporal

Aquí se pretende evaluar cómo se distribuye la cantidad de víctimas por: mes, franja horaria y día de la semana, mediante graficas se concluyó que los periodos de tiempo más criticos son: Diciembre, 5 AM y domingo de madrugada.

### 3. Análisis por ubicación

Descifrar los lugares donde hay más incidencias permite personalizar estrategias para prevenir muertes en carretera, después del análisis se evidencia que los sitios críticos son: las avenidas donde ocurren el 62% de los accidentes, donde la numero uno es la avenida General Paz, y por comuna la [1, 4, 9, 8].

Todas las graficas se pueden visualizar en [EDA](EDA.ipynb) 

Una vez limpios los datos se exportan a la herramienta de visualización ![Power BI](https://img.shields.io/badge/-Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=white)
donde a través de gráficos, indicadores, KPIs se puede hacer un `storytelling` para la audiencia involucrada en gestionar la prevención de muertes por accidentes de tránsito, y tener la información para poder tomar decisiones.

## KPI

En este apartado se consideran 3 KPIs los cuales fueron desarrollados en su totalidad desde Power BI

1. Reducir en un 10% la tasa de homicidios en siniestros viales de los últimos seis meses, en CABA, en comparación con la tasa de homicidios en siniestros viales del semestre anterior.
 
Se define la tasa de homicidios en siniestros viales como el número de víctimas fatales en accidentes de tránsito por cada 100,000 habitantes en un área geográfica durante un período de tiempo específico. Su fórmula es: (Número de homicidios en siniestros viales / Población total) * 100,000

Para desarrollarlo se pretende evaluar el segundo semestre con respecto al primero desde el año 2016 hasta el año 2021, se define  los cálculos matemáticos se desarrollan por medio de funciones DAX desde Power BI, las funciones empleadas se pueden visualizar en: [KPI_1](imagenes/kpi_1.png)


2. Reducir en un 7% la cantidad de accidentes mortales de motociclistas en el último año, en CABA, respecto al año anterior.

Se define a la cantidad de accidentes mortales de motociclistas en siniestros viales como el número absoluto de accidentes fatales en los que estuvieron involucradas víctimas que viajaban en moto en un determinado periodo temporal. Su fórmula para medir la evolución de los accidentes mortales con víctimas en moto es: (Número de accidentes mortales con víctimas en moto en el año anterior - Número de accidentes mortales con víctimas en moto en el año actual) / (Número de accidentes mortales con víctimas en moto en el año anterior) * 100
Las funciones empleadas se pueden visualizar en: [KPI_2](imagenes/kpi_2.png)

3. Reducir en un 5% la cantidad de accidentes que ocurren en las avenidas

Se define a la cantidad de accidentes mortales en avenidas como el número absoluto de accidentes fatales que ocurrieron en avenidas en un determinado periodo de tiempo, su fórmula para medir la evolución es: (Número de accidentes mortales con víctimas en avenidas en el año anterior - Número de accidentes mortales con víctimas en avenidas en el año actual) / (Número de accidentes mortales con víctimas en avenidas en el año anterior) * 100
Las funciones empleadas se pueden visualizar en:  [KPI_3](imagenes/kpi_3.png)


<div align="center">

![Imagen](imagenes/atencion..jpg)
## Conclusión
</div>

Después del revisar los hallazgos se hacen las siguientes recomendaciones: 

1. Implementar mas controles y dispositivos electrónicos para monitorear el límite de velocidad en avenidas.

2. Imponer multas más severas a los infractores, incluyendo peatones.

3. Educar a los conductores sobre las consecuencias de la conducción irresponsable y promover hábitos de seguridad vial.

4. Tolerancia de alcoholemia cero en sangre en los retenes policiales

5. Mejorar la calidad de la infraestructura vial, tales como señalización e iluminación.



Los esfuerzos conjuntos entre gobiernos, organismos de seguridad vial y ciudadanos podrían contribuir a reducir la cantidad de accidentes viales en las avenidas de Buenos Aires.


# Dashboard

[Visualizar el tablero](imagenes/siniestro_ultimo_copia.pbix)


