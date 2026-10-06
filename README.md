# Equivalency Between GARCH and RNN

**[Live page →](https://twinsilver.github.io/GARCH-RNN/)**

Demonstrates that a Recurrent Neural Network, when structurally constrained (identity activation, fixed output weights, parameter reparameterization), becomes mathematically equivalent to a GARCH(1,1) model. Fits both on XRP daily returns (2019–2026) and compares them via Value-at-Risk backtesting.

## Key findings

- Both models converge to nearly identical total volatility persistence (α + β ≈ 0.90), but reach it through different parameter splits — the RNN found a smoother, more persistent local minimum due to a flat likelihood surface.
- At 95% VaR, the RNN achieved 7.82% total violations vs. GARCH's 6.77%, closer to the 10% theoretical target — the classical MLE fit was more conservative (wider risk bounds) than necessary.
- Confirms that interpretability and the flexibility of a neural network training loop aren't mutually exclusive when the architecture is constrained to match a known statistical model.

## Stack

- Python, PyTorch (constrained RNN), `arch` (GARCH MLE baseline)
- Quarto (`.qmd` → self-contained HTML, `embed-resources: true`)

## Files

- `GARCH-RNN.qmd` — source document (code + writeup)
- `index.html` — rendered output, published via GitHub Pages
- `requirements.txt` — Python dependencies
- `XRP Historical Data.csv` — dataset

## Run locally

```
pip install -r requirements.txt
quarto render "GARCH-RNN.qmd" --output index.html
```
