# Bollinger Bands Strategy Code

```pinescript
//@version=6
strategy("Bollinger Bands Strategy", overlay=true)

length = input.int(20)
mult = input.float(2)

basis = ta.sma(close, length)
dev = mult * ta.stdev(close, length)

upper = basis + dev
lower = basis - dev

if ta.crossover(close, lower)
    strategy.entry("Long", strategy.long)

if ta.crossunder(close, upper)
    strategy.entry("Short", strategy.short)
