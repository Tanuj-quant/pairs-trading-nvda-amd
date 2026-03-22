# pairs-trading-nvda-amd
Statistical pairs trading strategy using NVDA and AMD based on z-score mean reversion.



# Pairs Trading Strategy: NVDA vs AMD

## Overview

This project implements a statistical pairs trading strategy using NVIDIA (NVDA) and AMD (AMD). The strategy identifies temporary deviations in the relationship between the two stocks and trades on the assumption that these deviations will revert to the mean.

The model uses a hedge ratio to construct a spread and applies a rolling z-score to detect trading opportunities.

---

## Strategy Logic

### 1. Hedge Ratio (β)

A linear regression is used to estimate the relationship between NVDA and AMD:

Spread = NVDA − β × AMD

---

### 2. Z-Score Calculation

The spread is standardized using a rolling window:

Z = (Spread − Mean) / Standard Deviation

---

### 3. Trading Rules

* **Z < -2** → Long spread

  * Buy NVDA
  * Sell AMD

* **Z > 2** → Short spread

  * Sell NVDA
  * Buy AMD

* **-0.5 < Z < 0.5** → Exit position

Signals are shifted forward by one period to avoid lookahead bias.

---

## Backtest Assumptions

* Initial capital: $10,000
* Capital split evenly between both legs of the trade
* No transaction costs or slippage (simplified model)
* Daily data used for backtesting
* Positions are entered and exited based on signal changes

---

## Results

* Final Capital: ~$11,295
* Total Return: ~13% over the test period

The results indicate modest profitability, suggesting the presence of weak mean reversion between NVDA and AMD.

---

## Key Learnings

* Proper position sizing is critical for realistic results
* Naive spread calculations can produce misleading performance
* Avoiding lookahead bias significantly impacts backtest validity
* Mean reversion exists but is not consistently strong

---

## Limitations

* Simplified execution model (no commissions or slippage)
* Single pair tested (NVDA/AMD only)
* Static hedge ratio (not recalculated over time)
* No risk management or stop-loss logic

---


