## Signos Vitales – Actividad 1 Big Data

Este proyecto corresponde a la Actividad 1 de la asignatura **Big Data (ID PREICA2502B020061)** de la Institución Universitaria Digital de Antioquia, orientada por el profesor **Andrés Felipe Callejas Jaramillo**. El objetivo es demostrar cómo una base de datos analítica puede apoyar al personal clínico al mostrar la última lectura válida de los signos vitales de cada paciente en una UCI, partiendo del conjunto de datos público `nasirayub2/human-vital-sign-dataset`.

- **Integrantes:** Jaider Morales Bautista, Aleicer Vesga Rueda.
- **Archivo principal:** `Signos Vitales.ipynb`.

### 1. Propósito

El cuaderno implementa un flujo que:
- Describe la problemática de consultar signos vitales recientes por paciente.
- Define el modelo entidad–relación propuesto (pacientes, mediciones, métricas derivadas y vista unificada).
- Descarga y prepara el dataset con `kagglehub` y `pandas`.
- Crea una tabla analítica en Spark y ejecuta consultas SQL para limpiar y obtener la lectura más reciente por paciente.

### 2. Requisitos previos

1. **Python 3.11 o superior** con las bibliotecas:
   - `kagglehub[pandas-datasets]>=0.3.8`
      - `pandas`
         - `pyspark` (el notebook asume que existe una sesión activa de Spark accesible como `spark`).
         2. **Credenciales de Kaggle** configuradas (token) para que `kagglehub` pueda descargar el dataset.
         3. Entorno de ejecución que soporte notebooks Jupyter y Spark (p. ej. Databricks, Jupyter con PySpark, o VS Code con extensión de Jupyter y Spark local).

         ### 3. Cómo usar el notebook

         1. Clona o descarga este repositorio.
         2. Abre `Signos Vitales.ipynb` en tu entorno Jupyter preferido.
         3. Verifica que la sesión de Spark (`spark`) esté creada antes de ejecutar las celdas relacionadas con SQL o tablas Spark.
         4. Ejecuta las celdas en orden. El notebook:
            - Instala dependencias necesarias.
               - Descarga automáticamente el dataset desde Kaggle.
                  - Lee el archivo CSV con `pandas`.
                     - Convierte la información a un DataFrame de Spark y la guarda como tabla `tbl_vital_signs`.
                        - Ejecuta consultas SQL que normalizan fechas y devuelven la última medición por paciente.

                        ### 4. Resultado esperado

                        Al finalizar la ejecución:
                        - Tendrás una tabla `tbl_vital_signs` en tu catálogo de Spark con los campos renombrados en formato analítico.
                        - Podrás ejecutar consultas SQL para identificar la lectura más reciente de cada paciente y validar la calidad de los datos de signos vitales.

                        ### 5. Contacto y créditos

                        - **Curso:** Big Data, Institución Universitaria Digital de Antioquia.
                        - **Profesor:** Andrés Felipe Callejas Jaramillo.
                        - **Equipo:** Jaider Morales Bautista, Aleicer Vesga Rueda.
                        