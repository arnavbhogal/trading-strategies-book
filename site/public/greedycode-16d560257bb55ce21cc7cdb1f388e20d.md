# Greedy Strategy Code

```pinescript
//@version=6
strategy("Greedy Strategy", pyramiding=100, overlay=true)

tp = input(10, "Take profit")
sl = input(10, "Stop loss")
maxidf = input(5, "Max intraday trades")

strategy.risk.max_intraday_filled_orders(maxidf)

upGap = open > high[1]
dnGap = open < low[1]

if upGap
    strategy.entry("GapUp", strategy.long, stop=high[1])

if dnGap
    strategy.entry("GapDn", strategy.short, stop=low[1])
