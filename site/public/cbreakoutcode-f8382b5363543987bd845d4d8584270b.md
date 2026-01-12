# Channel Breakout Code

```pinescript
//@version=6
strategy("ChannelBreakOutStrategy", overlay=true)

length = input.int(5)
upBound = ta.highest(high, length)
downBound = ta.lowest(low, length)

strategy.entry("Long", strategy.long, stop=upBound)
strategy.entry("Short", strategy.short, stop=downBound)
