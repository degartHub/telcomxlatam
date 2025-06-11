```markdown
# Análisis de Churn de Clientes - Telecom X

## Descripción
Este proyecto realiza un análisis exhaustivo del **churn de clientes** (abandono) para la empresa Telecom X, utilizando el conjunto de datos `TelecomX_Data.json`. El objetivo es identificar patrones y factores que contribuyen a la evasión de clientes, proporcionando insights y recomendaciones para mejorar la retención. El análisis incluye limpieza de datos, transformación, análisis descriptivo, visualizaciones, correlaciones, y un informe final en markdown con hallazgos y estrategias.

### Objetivos
- Limpiar y estandarizar el dataset, manejando valores nulos, duplicados, y formatos inconsistentes.
- Crear variables derivadas: `Cuentas_Diarias` (cargos mensuales ÷ 30) y `Cantidad_Servicios` (suma de servicios contratados).
- Realizar un análisis descriptivo de variables numéricas y categóricas.
- Analizar la distribución del churn y su relación con otras variables.
- Generar visualizaciones (histogramas, boxplots, barras apiladas, matriz de correlación, dispersión).
- Proporcionar un informe con conclusiones, insights, y recomendaciones estratégicas.

## Requisitos
El proyecto está diseñado para ejecutarse en **Google Colab** o un entorno Python local. Las bibliotecas necesarias son:

- Python 3.7+
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- IPython

En Google Colab, estas bibliotecas están preinstaladas. Si usas un entorno local, instala las dependencias con:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn ipython
```

## Estructura del Proyecto
```
TelecomX_Churn_Analysis/
├── figures/                        # Directorio con visualizaciones generadas (PNG)
├── TelecomX_Data_cleaned_transformed.csv  # Dataset limpio y transformado
├── TelecomX_numeric_descriptive.csv      # Estadísticas de variables numéricas
├── TelecomX_numeric_by_churn.csv         # Estadísticas numéricas por Abandono
├── TelecomX_correlation_matrix.csv       # Matriz de correlaciones
├── TelecomX_freq_*.csv                  # Frecuencias de variables categóricas
├── TelecomX_contingency_*.csv           # Tablas de contingencia por Abandono
├── churn_complete_analysis_with_error_fix_colab.py  # Script principal
└── README.md                    # Este archivo
```

## Instrucciones de Uso
### En Google Colab
1. Abre [Google Colab](https://colab.research.google.com/).
2. Crea un nuevo notebook.
3. Copia y pega el contenido de `churn_complete_analysis_with_error_fix_colab.py` en una celda.
4. Ejecuta la celda (Shift + Enter).
5. Verifica los resultados:
   - **Consola**: Estadísticas descriptivas, frecuencias, correlaciones, y lista de archivos guardados.
   - **Directorio `figures`**: 30 imágenes PNG (ej. `abandono_distribucion.png`).
   - **Archivos CSV**: Dataset transformado, estadísticas, y tablas.
   - **Informe**: Renderizado en markdown al final, con referencias a imágenes.
6. Descarga archivos (opcional):
   - En la pestaña "Archivos", haz clic derecho y selecciona "Descargar".
   - Para descargar todas las imágenes:
     ```python
     !zip -r figures.zip figures
     ```
     Descarga `figures.zip`.

### En un entorno local
1. Clona el repositorio o descarga `churn_complete_analysis_with_error_fix_colab.py`.
2. Asegúrate de tener las bibliotecas instaladas (ver Requisitos).
3. Ejecuta el script:
   ```bash
   python churn_complete_analysis_with_error_fix_colab.py
   ```
4. Los resultados se guardarán en el directorio actual (`figures/` y archivos CSV).

## Resultados
El script genera los siguientes outputs:

### Archivos Generados
- **Dataset transformado**: `TelecomX_Data_cleaned_transformed.csv`
- **Estadísticas numéricas**:
  - `TelecomX_numeric_descriptive.csv`: Media, mediana, std, min, max, IQR, skewness.
  - `TelecomX_numeric_by_churn.csv`: Métricas numéricas por `Abandono`.
- **Frecuencias categóricas**: `TelecomX_freq_*.csv` (ej. `TelecomX_freq_Abandono.csv`).
- **Tablas de contingencia**: `TelecomX_contingency_*.csv` (ej. `TelecomX_contingency_Tipo_Contrato.csv`).
- **Correlaciones**: `TelecomX_correlation_matrix.csv`.

### Visualizaciones
30 imágenes PNG en `figures/`:
- **Figura 1**: Distribución de `Abandono` (`abandono_distribucion.png`).
- **Figuras 2-17**: Abandono por categóricas (ej. `abandono_por_tipo_contrato.png`).
- **Figuras 18-22**: Boxplots de numéricas (ej. `boxplot_antiguedad_meses.png`).
- **Figuras 23-27**: Histogramas de numéricas (ej. `hist_cargos_mensuales.png`).
- **Figura 28**: Matriz de correlación (`correlation_matrix.png`).
- **Figuras 29-30**: Dispersión de `Cuentas_Diarias` y `Cantidad_Servicios` (`scatter_cuentas_diarias.png`, `scatter_cantidad_servicios.png`).

### Informe Final
Un informe en markdown al final del script, con:
- Introducción y objetivos.
- Descripción de la limpieza y transformación.
- Análisis exploratorio (descriptivo, distribuciones, correlaciones).
- Conclusiones: ~25-30% de churn, mayor en contratos mes a mes (~40-50%), fibra óptica (~40%), cheque electrónico (~40-50%).
- Insights: Clientes nuevos, con altos cargos, y contratos cortos son más propensos a abandonar.
- Recomendaciones: Incentivar contratos largos, optimizar fibra óptica, promover pagos automáticos, ofrecer servicios adicionales, y segmentar clientes de riesgo.
- Referencias a las 30 figuras.

### Hallazgos Clave
- **Tasa de churn**: ~25-30%.
- **Numéricas**:
  - `Antiguedad_Meses`: ~17 meses (churn) vs. ~40 meses (no churn).
  - `Cargos_Mensuales`: ~$75 (churn) vs. ~$60 (no churn).
  - `Cuentas_Diarias`: ~$2.50 (churn) vs. ~$2.00 (no churn).
  - `Cargos_Totales`: ~$1200 (churn) vs. ~$2800 (no churn).
  - `Cantidad_Servicios`: Similar (~2.5-2.7).
- **Categóricas**:
  - Mayor churn en contratos mes a mes, fibra óptica, y cheque electrónico.
  - Servicios como `Seguridad_Online` y `Soporte_Tecnico` reducen churn.
- **Correlaciones**:
  - Negativas: `Abandono` con `Antiguedad_Meses` (~-0.35), `Tipo_Contrato` (~-0.40).
  - Positivas: `Abandono` con `Cargos_Mensuales` (~0.20), `Servicio_Internet` (~0.25).

## Contribuir
Para extender el proyecto:
1. **Modelado predictivo**: Implementar un modelo de churn (ej. regresión logística, árboles de decisión).
2. **Segmentación**: Analizar subgrupos de clientes (ej. por antigüedad o servicios).
3. **Visualizaciones adicionales**: Generar gráficos interactivos (ej. con Plotly).
4. **Optimización**: Mejorar la eficiencia del código o añadir validaciones.

Crea un fork del repositorio, realiza los cambios, y envía un pull request con una descripción clara.

## Notas
- El dataset se carga desde una URL pública: [TelecomX_Data.json](https://raw.githubusercontent.com/ingridcristh/challenge2-data-science-LATAM/main/TelecomX_Data.json).
- En Google Colab, las imágenes se muestran con:
  ```python
  from IPython.display import Image, display
  display(Image(filename='figures/abandono_distribucion.png'))
  ```
- Si encuentras errores, verifica las versiones de las bibliotecas:
  ```python
  import pandas, numpy, matplotlib, seaborn, sklearn
  print("Pandas:", pandas.__version__)
  print("NumPy:", numpy.__version__)
  print("Matplotlib:", matplotlib.__version__)
  print("Seaborn:", seaborn.__version__)
  print("Scikit-learn:", sklearn.__version__)
  ```

## Autor
Desarrollado como parte de un análisis de datos para Telecom X, con código optimizado para Google Colab. Contacta para más detalles o colaboraciones.

## Licencia
MIT License - libre para usar, modificar, y distribuir con atribución.
```
