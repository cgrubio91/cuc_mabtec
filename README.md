# Unificación de Contratos de Interventoría - SECOP

Este proyecto automatiza la extracción, limpieza y unificación de datos de contratos de interventoría desde el Portal de Datos Abiertos de Colombia (Socrata). Consolida información de diferentes fuentes y años en un único repositorio procesado para análisis posterior.

## Descripción

El sistema realiza consultas a la API de Socrata (datos.gov.co) para obtener registros vinculados a procesos de interventoría entre los años 2015 y 2025. Integra datos provenientes de múltiples esquemas de información (incluyendo SECOP I y SECOP II), estandarizando columnas y formatos de fecha para asegurar la integridad del dataset final.

## Requisitos

El proyecto está desarrollado en Python y requiere las siguientes librerías:

- pandas: Para la manipulación y normalización de estructuras de datos.
- requests: Para la gestión de peticiones HTTP a la API de datos abiertos.
- tqdm: Para el monitoreo del progreso durante las descargas masivas.
- openpyxl: Necesario para la exportación de resultados a formato Excel.

## Instalación

1. Clonar el repositorio.
2. Instalar las dependencias listadas en el archivo de requerimientos:
   ```bash
   pip install -r requirements.txt
   ```

## Estructura del Proyecto

- `CUC.ipynb`: Notebook principal que contiene la lógica de descarga, preprocesamiento y unión.
- `requirements.txt`: Listado de librerías necesarias.
- `data/`: Directorio destinado al almacenamiento de archivos intermedios o crudos.
- `df_unido.xlsx`: Archivo de salida que contiene la base de datos consolidada.

## Proceso de Ejecución

El flujo de trabajo automatizado en el notebook sigue estos pasos:

1. **Configuración de Fuentes**: Definición de endpoints y parámetros de búsqueda para contratos con el descriptor 'Interventoría'.
2. **Extracción Paginada**: Descarga de registros en lotes para evitar límites de la API, cubriendo el rango de años 2015-2025.
3. **Limpieza y Estandarización**:
   - Eliminación de espacios en blanco en campos de texto.
   - Conversión de formatos de fecha a objetos datetime.
   - Normalización de valores monetarios a formato numérico flotante.
   - Homologación de nombres de columnas entre distintas fuentes de datos.
4. **Exportación**: Generación del archivo Excel unificado con toda la información procesada.
