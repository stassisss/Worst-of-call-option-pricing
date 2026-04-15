## Project description

### Worst-of Call Option Pricing — NVDA x AVGO

Pricing and risk analysis of a multi-asset exotic derivative using
Monte Carlo simulation on real market data.

### Overview

A **Worst-of Call** pays the return of the worse performer of two
underlying assets at maturity - this makes it cheaper than a vanilla call
but exposed to correlation risk. This project prices a 6-month ATM
Worst-of Call on NVIDIA (NVDA) and Broadcom (AVGO), two correlated
AI-infrastructure equities.

### Methodology

- **Market data:** spot prices, historical volatilities, and
  correlation estimated from 1-year daily returns via `yfinance`
- **Pricing:** Monte Carlo simulation (500k paths) under the risk-neutral measure;
  correlated GBM paths generated via Cholesky decomposition
- **Benchmark:** compared against individual Black-Scholes vanilla
  calls to quantify the worst-of discount
- **Greeks:** computed with central finite differences (bumping) 
- **Correlation sensitivity:** option price presented under different correlations [−0.8, 0.95] (confirms Long correlation position)
- **Risk management:** the main considerations include negative gamma, correlation risk (long corr.),
  and worst-of drag.

### Results

| | Price (% of notional) |
|---|---|
| NVDA vanilla call | 12.02% |
| AVGO vanilla call | 13.85% |
| Worst-of call | 7.31% |

NVDA $\delta$ = 0.2278  
AVGO $\delta$ = 0.1752  
*Gamma* for both < 0 (negative convexity)  
*Cross-gamma* = 0.927

### Stack (main libraries used)

Python · NumPy · SciPy · yfinance · Matplotlib

Market data is fetched live via `yfinance` library; re-running will reflect current
spot prices and volatilities.

---

**Google Colab**:  
*[https://colab.research.google.com/github/stassisss/Worst-of-call-option-pricing/blob/main/exotic_option_project_worst_of_call_NVDA_AVGO](https://colab.research.google.com/github/stassisss/Worst-of-call-option-pricing/blob/main/exotic_option_project_worst_of_call_NVDA_AVGO)*

--- 

## Описание на русском языке

### Оценка Worst-of Call опциона — NVDA x AVGO

Ценообразование и анализ рисков многоактивного экзотического
опциона методом Монте-Карло на реальных рыночных данных.

**Worst-of Call** выплачивает доходность худшего из двух базовых
активов на дату экспирации; это делает его дешевле vanilla call,
но создаёт дополнительную подверженность correlation risk.
В проекте оценивается 6-месячный ATM Worst-of Call на NVIDIA (NVDA)
и Broadcom (AVGO) — двух коррелированных компаний из
AI-инфраструктурного сектора.

### Методология

- **Рыночные данные:** спот-цены, исторические волатильности и
  корреляция через `yfinance`
- **Ценообразование:** симуляция Монте-Карло (500k траекторий) в
  риск-нейтральной мере; коррелированные GBM-траектории генерируются
  через разложение Холецкого
- **Бенчмарк:** сравнение с vanilla call по формуле Блэка-Шоулза
  для количественной оценки worst-of дисконта
- **Greeks:** греки вычислены методом центральных конечных разностей
  (bumping)
- **Анализ чувствительности:** зависимость цены опциона от разных значений корреляции на промежутке [−0.8, 0.95]
- **Риск-менеджмент:** основные риски включают отрицательную выпуклость (negative gamma),
  correlation risk, и worst-of drag
  
### Результаты

| | Цена (% от номинала) |
|---|---|
| NVDA vanilla call | 12.02% |
| AVGO vanilla call | 13.85% |
| Worst-of call     | 7.31% |

NVDA $\delta$ = 0.2278  
AVGO $\delta$ = 0.1752  
*Gamma* для обоих < 0 (отрицательная выпуклость)  
*Cross-gamma* = 0.927

### Основные библиотеки

Python · NumPy · SciPy · yfinance · Matplotlib

Рыночные данные загружаются в реальном времени через библиотеку `yfinance`; при повторном
запуске будут использованы актуальные значения.
