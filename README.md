# telecom-analysis
Este proyecto desarrolla un análisis exhaustivo y un proceso de *data wrangling* / limpieza sobre la base de usuarios e interacciones de **ConnectaTel**. El objetivo principal es identificar la calidad de los datos, corregir anomalías estructurales y operativas, y segmentar a los clientes según su comportamiento de consumo para optimizar la estrategia de monetización y conversión de planes.

## 🎯 Objetivo del Proyecto

* **Saneamiento de Datos:** Identificar, diagnosticar y corregir valores nulos ocultos, inconsistencias lógicas en fechas, valores centinela (`-999` en edad) y mitigar el impacto de *outliers* de infraestructura ("llamadas fantasma").
* **Análisis Exploratorio de Datos (EDA):** Examinar las distribuciones demográficas y de uso para descubrir patrones de comportamiento en los canales de llamadas y mensajería.
* **Segmentación de Clientes:** Mapear el comportamiento de los usuarios según categorías de Edad y Nivel de Uso para proveer *insights* estratégicos y recomendaciones de negocio orientadas al *upselling* del Plan Premium.

## 📊 Datasets Utilizados

El análisis se fundamenta en el cruce de datos transaccionales y de perfil de usuario:
1. **`user_profile` (Datos de Usuarios):** Contiene información demográfica como ID de usuario, edad, ciudad de registro, fecha de alta y el plan contratado (`Basico` o `Premium`).
2. **Tabla de Interacciones (Datos Transaccionales):** Registro detallado de 40,000 interacciones que incluye la fecha de consumo, el tipo de comunicación (`call` o `text`), la duración en minutos y la longitud de caracteres.
---

## 🛠️ Etapas del Análisis Realizadas

El flujo de trabajo en el Notebook está estructurado en las siguientes fases críticas:

1. **Diagnóstico y Calidad de Datos (*Data Wrangling*):**
   * Detección e imputación con la mediana de valores centinela (`-999`) en la variable `age`.
   * Limpieza de nulos ocultos (`?`) y mapeo de un 11.7% de registros faltantes en `city`.
   * Corrección de inconsistencias de fechas futuras (registros del año 2026).
   * Tratamiento de valores ausentes condicionales tipo **MAR (Missing at Random)** en las métricas de `duration` y `length`.

2. **Análisis de Distribuciones Estadísticas:**
   * Evaluación de variables continuas y discretas mediante histogramas y curvas de densidad (KDE).
   * Identificación de la asimetría positiva (sesgo a la derecha) en el volumen de mensajes, llamadas y duración.

3. **Análisis de Dispersión y Outliers:**
   * Implementación de Diagramas de Caja y Bigotes (**Boxplots**) para definir matemáticamente los umbrales de comportamiento normal frente a consumos atípicos.
   * Aislamiento de 109 "llamadas fantasma" (registros erróneos de hasta 155 minutos) en el Plan Básico.

4. **Agrupamiento y Segmentación Categórica (*Binning*):**
   * Creación y visualización de perfiles consolidados por grupos de Edad (`Joven`, `Adulto`, `Adulto Mayor`) y Nivel de Uso (`Bajo uso`, `Uso medio`, `Alto uso`).

## ▶ Cómo abrir el notebook en Google Colab

Haz clic en el siguiente botón:

(https://github.com/linamoyano21-maker/telecom-analysis)

O:

1. Abre el archivo `.ipynb` en GitHub
2. Haz clic en **Open in Colab**

## 📘 Cómo reproducir el análisis

1. Abre `notebooks/everpeak_analysis.ipynb`
2. Ejecuta las celdas en orden
3. El notebook carga automáticamente el dataset desde `/data/` o desde un enlace público (según corresponda)
