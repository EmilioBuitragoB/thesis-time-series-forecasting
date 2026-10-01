# 📈 Rentabilidad y volatilidad de fondos sostenibles (FIS) vs. tradicionales (FIC) en Colombia (2023–2025)

*English summary: forecasting return and volatility of sustainable (FIS) vs. traditional (FIC) mutual funds in Colombia using ARIMA, GARCH, Prophet and LSTM. Master's thesis, Universidad de La Salle.*

## Contexto
Trabajo de grado de la Maestría en Analítica e Inteligencia de Negocios (Universidad de La Salle), desarrollado en equipo con Tatiana Flórez y Viviana Espinosa y dirigido por Leandro Vivas.

**Mi contribución:** el código en Python de este repositorio — pruebas estadísticas, modelos de pronóstico de rentabilidad y modelos de pronóstico de volatilidad. La investigación, el marco teórico y la sustentación fueron trabajo conjunto del equipo.

**Pregunta de investigación:** ¿son los Fondos de Inversión Sostenibles (FIS) una mejor alternativa que los Fondos de Inversión Tradicionales (FIC) en Colombia, en términos de rentabilidad y volatilidad?

## Datos y metodología
- **Muestra:** 4 fondos de las mismas administradoras — 2 FIC (BBVA FAM, Valor Plus I) y 2 FIS (BBVA Páramo, Sostenible Global).
- **Periodo:** 24 sep. 2023 – 30 sep. 2025, observaciones diarias. Fuente: Asofiduciarias.
- **Enfoque:** cuantitativo, positivista, comparativo longitudinal.
- **Diagnóstico estadístico:** estacionariedad (ADF, Phillips-Perron), autocorrelación (Ljung-Box), normalidad (Jarque-Bera, Shapiro-Wilk), heterocedasticidad condicional (ARCH-LM). Todas las series resultaron estacionarias en niveles I(0); se rechazó la normalidad en todos los fondos (distribuciones leptocúrticas); se confirmó agrupamiento de volatilidad (volatility clustering).
- **Modelos:** AutoARIMA, Prophet, GARCH y LSTM, con partición cronológica 80/20 y optimización de hiperparámetros por grid search, minimizando RMSE.
- **Desempeño ajustado por riesgo:** Sharpe, Treynor, Alfa de Jensen, M², Sortino, máximo drawdown y valor de Shapley.

## Resultados

**Rentabilidad y volatilidad promedio (% E.A.)**

| Fondo | Tipo | Rentabilidad | Volatilidad |
|---|---|---|---|
| BBVA FAM | FIC | 9,4% | 0,54% |
| Valor Plus I | FIC | 9,3% | 0,36% |
| BBVA Páramo | FIS | 10,8% | 3,77% |
| Sostenible Global | FIS | 17,5% | 13,45% |

**Desempeño ajustado por riesgo**

| Indicador | Valor Plus I | BBVA FAM | BBVA Páramo | Sostenible Global |
|---|---|---|---|---|
| Sharpe | 1,69 | 1,44 | 0,47 | 0,42 |
| Sortino | 2,01 | 1,28 | 0,69 | 0,65 |
| Máx. drawdown | -14,65% | -19,16% | -54,02% | -89,14% |

En la mayoría de los indicadores, **los FIC mostraron mejor desempeño ajustado por riesgo** que los FIS.

**Pronóstico**
- Rentabilidad: ARIMA fue el modelo ganador en los 3 fondos más estables (RMSE entre 2,28 y 13,16); en el fondo más volátil (Sostenible Global), LSTM redujo el RMSE a 20,74 frente a ~46,66 de los modelos clásicos.
- Volatilidad: LSTM superó a GARCH en los 4 fondos.

## Hallazgos principales
1. Los FIS rindieron más en términos absolutos, pero con volatilidad significativamente mayor (hasta 37× superior en el caso más extremo).
2. En esta muestra, los FIC ofrecieron mejor desempeño ajustado por riesgo — más adecuados para perfiles conservadores.
3. Los modelos de aprendizaje profundo (LSTM) y los econométricos clásicos (ARIMA, GARCH) son complementarios: ARIMA funciona mejor en series estables, LSTM en series más volátiles y no lineales.
4. La mayor rentabilidad de los FIS puede justificar su mayor riesgo para inversionistas que priorizan criterios ASG.

## Limitaciones
Muestra exploratoria: solo 2 FIS con historial de datos abiertos representativos en Colombia, y series históricas cortas (afectan el aprendizaje del LSTM). Los resultados son evidencia preliminar y no deben generalizarse.

## Estructura
1. `01_pruebas_estadisticas.ipynb`: estacionariedad, normalidad, autocorrelación y heterocedasticidad.
2. `02_modelos_rentabilidad.ipynb`: pronóstico de rentabilidad (ARIMA, Prophet).
3. `03_modelos_volatilidad.ipynb`: pronóstico de volatilidad (GARCH, LSTM).

## Tecnologías
Python · pandas, statsmodels, arch, prophet, scikit-learn, tensorflow/keras, Google Colab

## Cómo ejecutarlo
Instala las dependencias con `pip install -r requirements.txt` y abre los notebooks en orden, o directamente en Colab.
