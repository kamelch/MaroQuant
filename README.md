# MaroQuant Strategies for Freqtrade

A collection of custom algorithmic trading strategies designed for the [Freqtrade](https://www.freqtrade.io/) crypto trading bot. This pack includes trend-following, mean-reversion, and hybrid regime-switching algorithms optimized for various timeframes.

## 🧠 Strategy Overview

### 1. `bollinger_macd_adx_4h.py` (The Hybrid)
**Timeframe:** 4h
**Concept:** Market Regime Switching.
* **Ranging Market (Low ADX):** Uses **Bollinger Bands** to trade mean reversion (buy low, sell high).
* **Trending Market (High ADX):** Switches to **MACD** to catch strong breakouts and trend continuations.
* **Why it works:** Adapts to changing market conditions rather than forcing a single logic type.

### 2. `macd_adx_4h.py` (Trend Follower)
**Timeframe:** 4h
**Concept:** Pure Trend Following.
* **Entry:** Requires MACD Histogram crossover **AND** strong trend strength (ADX > 25) with positive directional movement (DI+ > DI-).
* **Exit:** Detects trend exhaustion via MACD and directional reversal.
* **Risk:** Wide stop-loss (-100%), relying on the strategy's sell signal to close trades dynamically.

### 3. `macd_stddev_5m.py` (Standard Dev Reversal)
**Timeframe:** 5m (High Frequency)
**Concept:** Volatility-Adjusted Momentum.
* **Logic:** Identifies potential reversals by combining MACD histogram inflection points with Standard Deviation (`STDDEV`) analysis.
* **Risk Management:** Tighter stop-loss (-21%) and stepped ROI for quick scalping.

### 4. `ema_crossover_5m.py` (Custom Oscillator)
**Timeframe:** 5m
**Concept:** Composite EMA Crossover.
* **Logic:** *Note: Despite the filename, this strategy uses a custom EMA weighting system, not Bollinger Bands.*
* It calculates a weighted blend of fast (9/18) and slow (32/64) EMA differentials to create a custom momentum oscillator for signal generation.

---

## 🛠️ Installation

1.  **Requirement:** Ensure you have a working [Freqtrade](https://www.freqtrade.io/en/stable/installation/) installation.
2.  **Deploy:** Copy the `.py` files into your Freqtrade user data folder:
    ```bash
    cp *.py /path/to/freqtrade/user_data/strategies/
    ```
3.  **Run:** Launch Freqtrade with your desired strategy:
    ```bash
    freqtrade trade --strategy Maro4hBbAdxMacd
    ```

---

## ⚙️ Configuration Hints

* **Timeframes:** Strategies are hardcoded for `4h` or `5m`. Ensure your config file provides data for these candles.
* **Pairs:** `Maro4h_Macd_Adx` and the Hybrid strategy specifically request informative pairs (BTC/USD, ETH/USD) for trend confirmation.
* **Libraries:** Requires `talib`, `numpy`, and `freqtrade` standard libraries.

---

## ⚠️ Disclaimer

These strategies are for educational purposes. Cryptocurrency trading involves high risk. **Always backtest** extensively (`freqtrade backtesting ...`) and run in **Dry Run** mode before deploying real capital.
