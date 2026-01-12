# MACD Strategy Code

```pinescript
//@version=6
strategy("MACD Strategy", overlay=true)

fastLength = input(12, "Fast length")
slowlength = input(26, "Slow length")
MACDLength = input(9, "MACD length")

MACD = ta.ema(close, fastLength) - ta.ema(close, slowlength)
aMACD = ta.ema(MACD, MACDLength)
delta = MACD - aMACD

if ta.crossover(delta, 0)
    strategy.entry("MacdLE", strategy.long)

if ta.crossunder(delta, 0)
    strategy.entry("MacdSE", strategy.short)
