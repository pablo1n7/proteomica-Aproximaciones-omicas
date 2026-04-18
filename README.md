# Proteómica - Aproximaciones Ómicas
### Análisis de expresión diferencial y reajuste metabólico en *Cupriavidus necator* rGlyP

Este repositorio contiene el flujo de trabajo computacional completo para el procesamiento y análisis de datos de proteómica cuantitativa (adquisición DIA) obtenidos mediante espectrometría de masas (Orbitrap Exploris 480). El objetivo central es validar la integración funcional de la vía sintética rGlyP y caracterizar el reajuste del proteoma frente al ciclo nativo CBB.

## 🚀 Estructura del Proyecto

El análisis se ha organizado en una serie de Notebooks de Jupyter que garantizan la trazabilidad del dato, desde la matriz cruda hasta el análisis de enriquecimiento funcional:

1. **`01-preprocesamiento.ipynb`**: Carga de datos, limpieza de contaminantes y estructuración inicial.
2. **`02-filtro-peptido.ipynb`**: Filtrado técnico restrictivo (umbral de 4 péptidos únicos) para asegurar la fiabilidad de las proteínas identificadas.
3. **`03-completar-perdidos.ipynb`**: Gestión de valores faltantes mediante imputación condicional con distribución normal desplazada (width 0.3, shift 1.8).
4. **`04-agregar-anotaciones.ipynb`**: Integración de metadatos desde UniProt y mapeo de identificadores.
5. **`05-pca.ipynb`**: Análisis de Componentes Principales para validar la segregación biológica y la consistencia de las réplicas.
6. **`06-two-samples-tests.ipynb`**: Análisis de expresión diferencial mediante T-test con corrección de Benjamini-Hochberg (FDR).
7. **`07-plot.ipynb`**: Generación de visualizaciones avanzadas (Volcano Plots, Clustermaps y perfiles de expresión).
8. **`08-goterms.ipynb`**: Análisis de enriquecimiento funcional (Gene Ontology) para identificar los procesos biológicos clave.

## 📊 Metodología y Criterios

* **Filtro de calidad:** Se conservaron proteínas detectadas en al menos 2 de las 3 réplicas biológicas por condición.
* **Significancia:** Se consideraron proteínas diferencialmente expresadas (DEPs) aquellas con $|log_{2}FC| > 1$ y $p_{adj} < 0.05$.
* **Enriquecimiento:** Los términos GO se filtraron utilizando un umbral de significancia estadística basado en FDR.

## 🛠️ Instalación y Requisitos

Para replicar este análisis, se recomienda el uso de Python 3.8+ y las siguientes dependencias:

```bash
pip install pandas numpy matplotlib seaborn scipy statsmodels scikit-learn
