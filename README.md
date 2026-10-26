# Análisis Estadístico y Exploratorio de Datos (EDA) - ConnectaTel

## 🎯 Objetivo del proyecto
Este proyecto tiene como objetivo realizar una limpieza profunda, preprocesamiento, análisis exploratorio de datos (EDA) y segmentación de clientes para la empresa de telecomunicaciones **ConnectaTel**, transformando datos sin procesar en insights accionables para la toma de decisiones estratégicas de negocio.

## 📂 Datasets utilizados
El proyecto integra tres fuentes de datos principales:
- **`users` (o `users_latam`):** Contiene la información demográfica, ubicación, fechas de registro y tipo de plan (`Basico` o `Premium`) de los clientes.
- **`plans`:** Catálogo con los detalles generales de los planes de la compañía.
- **`usage`:** Registro detallado de la actividad de consumo histórico de los usuarios (tipo de servicio, duración de llamadas, cantidad de mensajes y fechas).

## 📊 Etapas del análisis realizadas
1. **Auditoría y Exploración Inicial:** Inspección de tipos de datos, conteo de valores nulos y detección de anomalías estructurales.
2. **Tratamiento de Valores Inválidos y Sentinels:** 
   - Reemplazo de edades con valores centinela (`-999`) por la mediana de la distribución.
   - Estandarización de formatos de fecha y conversión de fechas futuras erróneas (año 2026) a nulos (`NaT`).
   - Limpieza de caracteres inválidos (`?`) en las columnas de ubicación (`city`).
3. **Análisis de Nulos (MAR):** Verificación de la aleatoriedad de los nulos en duración y longitud de llamadas en función de la variable `type`, manteniéndolos como nulos estructurales válidos.
4. **Agregación y Combinación (Merge):** Agregación de la tabla de uso por `user_id` para calcular métricas clave (`cant_mensajes`, `cant_llamadas`, `cant_minutos_llamada`) y su posterior unión con el perfil de usuarios mediante un `left join`.
5. **Visualización de Distribuciones:** Generación de histogramas segmentados por tipo de plan (`hue='plan'`) para evaluar la normalidad, sesgos y posibles diferencias demográficas o de consumo.
6. **Detección y Tratamiento de Outliers:** Identificación de valores extremos mediante diagramas de caja (Boxplots) y cálculo de límites con el método IQR, evaluando su impacto comercial.
7. **Segmentación de Clientes:** Creación de categorías basadas en el nivel de uso (`grupo_uso`) y grupos etarios (`grupo_edad`).
8. **Conclusiones Ejecutivas:** Síntesis de hallazgos estratégicos y recomendaciones orientadas a los *stakeholders*.

## 🚀 Cómo ejecutar el proyecto
Puedes revisar y ejecutar este análisis de forma interactiva directamente en tu navegador:
1. Haz clic en el botón de apertura en Google Colab (si tienes la insignia configurada) o descarga el archivo `.ipynb` desde este repositorio.
2. Sube el notebook a tu entorno de Google Colab junto con los archivos CSV de los datasets en el directorio correspondiente.
3. Ejecuta las celdas secuencialmente de arriba hacia abajo para replicar las transformaciones, gráficos y conclusiones.

## 📝 Guía de reproducción
- Asegúrate de contar con un entorno de Python con las librerías estándar de ciencia de datos instaladas: `pandas`, `numpy`, `matplotlib` y `seaborn`.
- Respeta el orden de ejecución de las celdas, ya que las transformaciones de limpieza y los *merges* alimentan directamente las etapas de visualización y segmentación.
