# Signos Vitales – Actividad 1 Big Data

Este proyecto corresponde a la *Actividad 1* de la asignatura **Big Data (ID PREICA2502B020061)** de la Institución Universitaria Digital de Antioquia, orientada por el profesor **Andrés Felipe Callejas Jaramillo**.  
El objetivo es demostrar cómo una base de datos analítica puede apoyar al personal clínico al mostrar la última lectura válida de los signos vitales de cada paciente en una UCI, utilizando el dataset público **nasirayub2/human-vital-sign-dataset**.

**Integrantes:** Jaider Morales Bautista, Aleicer Vesga Rueda  
**Archivo principal:** `Signos Vitales.ipynb`

---

## 1. Propósito

El cuaderno implementa un flujo que:

- Describe la problemática de consultar signos vitales recientes por paciente.
- Define el modelo entidad–relación propuesto (pacientes, mediciones, métricas derivadas y vista unificada).
- Descarga y prepara el dataset con `kagglehub` y `pandas`.
- Crea una tabla analítica en Spark y ejecuta consultas SQL para limpiar y obtener la lectura más reciente por paciente.

---

## 2. Requisitos previos

**Python 3.11 o superior**, con las bibliotecas:

- `kagglehub[pandas-datasets]>=0.3.8`
- `pandas`
- `pyspark`  
  *(el notebook asume una sesión activa de Spark accesible como `spark`)*

**Además:**

- Credenciales de Kaggle configuradas para permitir la descarga con kagglehub.
- Entorno compatible con Jupyter y Spark (Databricks, JupyterLab con kernel Spark local, etc.).

---

## 3. Cómo usar el notebook

1. Clona o descarga este repositorio.  
2. Abre `Signos Vitales.ipynb` en tu entorno Jupyter preferido.  
3. Verifica que la sesión de Spark (`spark`) esté creada antes de ejecutar celdas SQL.  
4. Ejecuta todas las celdas en orden. El notebook:

   - Instala dependencias necesarias.  
   - Descarga automáticamente el dataset desde Kaggle.  
   - Lee el archivo CSV con `pandas`.  
   - Convierte la información a un DataFrame de Spark y la guarda como tabla `tbl_vital_signs`.  
   - Ejecuta consultas SQL para normalizar fechas y obtener la última medición por paciente.

---

## 4. Resultado esperado

Al finalizar la ejecución:

- Obtendrás una tabla **`tbl_vital_signs`** en tu catálogo de Spark con campos renombrados en formato analítico.
- Podrás ejecutar consultas SQL para identificar la lectura más reciente de cada paciente y validar la calidad de los datos.

---

## 5. Contacto y créditos

**Curso:** Big Data – Institución Universitaria Digital de Antioquia  
**Profesor:** Andrés Felipe Callejas Jaramillo  
**Equipo:** Jaider Morales Bautista, Aleicer Vesga Rueda

---

# Actividad 2: Despliegue e Ingesta en Databricks con SQL

En esta segunda fase, se migró la solución a una infraestructura cloud utilizando **Databricks Community Edition**.  
El desarrollo se centró exclusivamente en **Spark SQL** y herramientas nativas de Databricks para el manejo del ciclo de vida de los datos (diseño, carga y validación), siguiendo un paradigma **SQL-First**.

**Archivo principal:** `actividad_2.ipynb`  
**Dataset:** Human Vital Signs Dataset

---

## 1. Objetivos y Alcance

El objetivo principal fue establecer una arquitectura base en la nube (*Bronze Layer*):

### Diseño de Esquema (DDL)
- Definición de tabla mediante `CREATE TABLE` con tipos estrictos (`INT`, `TIMESTAMP`, `DOUBLE`).
- Inclusión de comentarios por columna para asegurar integridad y claridad del modelo.

### Configuración de Infraestructura
- Documentación del clúster Spark en Databricks.
- Uso de **DBFS/Volumes** para gestionar el dataset fuente.

### Ingesta de Datos con SQL
- Carga y transformación de los datos crudos (CSV) hacia tablas Delta.
- Normalización de nombres de columnas.
- Casteo adecuado de tipos.

### Validación Analítica
- Consultas SQL con `SELECT`, `GROUP BY` y funciones agregadas.
- Obtención de insights preliminares como promedios por categoría de riesgo.

### Análisis Comparativo
- Evaluación conceptual de ventajas y desventajas del enfoque SQL frente a otros paradigmas de Big Data basados en código (Spark API).

---

## 2. Tecnologías Utilizadas

- **Databricks Community Edition**
- **Spark SQL**
- **Databricks File System (DBFS) / Volumes**
- **Delta Lake**

---

## 3. Resultados

- Creación exitosa de tablas persistentes en el catálogo de Databricks.
- Pipeline de ingestión completamente funcional mediante SQL.
- Documentación visual del esquema y análisis comparativo dentro del notebook.

---

# Actividad 3: Proyecto Integrador

En esta tercera fase, se implementó un proyecto integrador que consolida los conocimientos adquiridos en las actividades anteriores, enfocándose en la organización de datos mediante catálogos, transformaciones avanzadas y visualización analítica.

**Integrantes:** Jaider Morales Bautista, Aleicer Vesga Rueda  
**Archivo principal:** `Actividad_3.ipynb`
**Link video:** [![Ver video](https://img.shields.io/badge/Ver%20Video-Google%20Drive-blue?style=for-the-badge&logo=google-drive)](https://drive.google.com/file/d/1F-CyM7R5dNGynrQerY-cfZaDPH_Xe_50/view?usp=sharing)

---

## Resumen

La actividad consistió en la creación de un catálogo y esquema estructurado (`salud_digital.vital_sign`) en Databricks para organizar los datos de signos vitales. Se implementaron transformaciones de fecha para extraer componentes temporales (año, mes, día, día de la semana) y se generó un resumen mensual con agregaciones estadísticas. Se realizó una limpieza exhaustiva de datos aplicando validaciones de rangos clínicos, normalización de valores y técnicas de imputación para variables como temperatura corporal, frecuencia cardíaca, saturación de oxígeno y edad. Finalmente, se desarrollaron visualizaciones analíticas utilizando librerías Python (matplotlib, plotly, seaborn) para explorar distribuciones por género, tendencias temporales de temperatura y patrones de mediciones por día de la semana, comparando además las implementaciones en SQL y PySpark para demostrar la equivalencia entre ambos paradigmas.

---
