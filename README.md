# 📈 Rentabilidad y volatilidad de fondos sostenibles (FIS) vs. tradicionales (FIC) en Colombia

*English summary: forecasting return and volatility of sustainable (FIS) vs. traditional (FIC) mutual funds in Colombia (2023–2025) using ARIMA, GARCH, Prophet and LSTM. Master's thesis, Universidad de La Salle.*

## Contexto
Trabajo de grado de la Maestría en Analítica e Inteligencia de Negocios (Universidad de La Salle)

**Mi contribución:** el código en Python de este repositorio (pruebas estadísticas, modelos de rentabilidad y modelos de volatilidad). La investigación, el marco teórico y la sustentación fueron trabajo conjunto del equipo.

**Pregunta de investigación:** ¿son los fondos de inversión sostenibles (FIS) una mejor alternativa que los tradicionales (FIC) en términos de rentabilidad y volatilidad en Colombia?

## Datos y metodología
- **Muestra:** 4 fondos, 2 FIS (BBVA Páramo, Sostenible Global) y 2 FIC (BBVA FAM, Valor Plus I) de las mismas administradoras.
- **Periodo:** 24 sep 2023 – 30 sep 2025, observaciones diarias. Fuente: Asofiduciarias.
- **Diagnóstico estadístico:** ADF y Phillips-Perron (estacionariedad), Ljung-Box (autocorrelación), Jarque-Bera y Shapiro-Wilk (normalidad), ARCH-LM (heterocedasticidad).
- **Modelos:** AutoARIMA, Prophet, GARCH y LSTM, con partición cronológica 80/20, búsqueda en malla de hiperparámetros y evaluación con RMSE y MAE.
- **Pronóstico de rentabilidad:** ARIMA fue el mejor modelo en 3 de 4 fondos; LSTM ganó en el más volátil (Sostenible Global, RMSE 20,74 frente a 46,66 de los modelos clásicos).
- **Pronóstico de volatilidad:** LSTM superó a GARCH en los cuatro fondos.

## Limitaciones
Muestra exploratoria (solo 2 FIS con historial suficiente) y series cortas, que afectan el aprendizaje del LSTM. Los resultados son evidencia preliminar y no deben generalizarse.

## Estructura
1. `01_pruebas_estadisticas.ipynb`: estacionariedad, normalidad, autocorrelación y residuos.
2. `02_modelos_rentabilidad.ipynb`: pronóstico de rentabilidad.
3. `03_modelos_volatilidad.ipynb`: modelado y pronóstico de volatilidad.

## Tecnologías
Python · Google Colab

## Cómo ejecutarlo
Instala las dependencias con `pip install -r requirements.txt` y abre los notebooks en orden, o directamente en Colab.
