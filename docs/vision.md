# Trading Cockpit: Vision Document

Working title. Draft v1, 6 October 2026. Builds on the Argus and Jarvis projects.

## 1. The one-line vision

A simple, calm, Kraken-style trading screen where I read the market the way I always have (candles and MACD), and make the decision myself with two buttons: Buy and Sell. The machine does everything else: watching, calculating, protecting, and keeping the books.

## 2. Why this, and why now

Argus and Jarvis set out to answer a big question: can a system watch crypto markets continuously, find profitable opportunities, trade them, and generate sustainable returns without me staring at charts all day?

What we learned:

- Building an automated trading system is largely solved. Exchange connectivity, market data, indicators, scanning, order execution, position management, stops and targets, monitoring and bookkeeping were built in Jarvis.

- A reliable, provable edge was not found. Argus explored price action, MACD, momentum, volume, regimes and selection rules. Some tests looked promising, but nothing survived rigorous testing. When to trade stayed unresolved.

The cockpit is a third direction. Keep the plumbing, put the human back in as the decision engine, and let the machine remove the hassle. I have made money trading by reading charts before, so this builds the tool around how I already trade rather than trying to encode my judgement into an algorithm.

## 3. Principles

1. I decide, the machine doesn't. No autonomous trading. Nothing is bought or sold without me pressing the button.

2. Brutally simple. Kraken-style simplicity, without the clutter of Kraken Pro's interface. If a feature doesn't make a decision or an action easier, it doesn't go on the main screen.

3. Protect me from the boring disasters. Fees, slippage, unprotected positions, and bad days are handled by design, not by willpower.

4. Honest numbers. Profit and loss is always shown after fees. Nothing on screen looks more certain than it really is.

5. Reuse, don't rebuild. Jarvis's exchange plumbing is the foundation.

## 4. The core screen

The main screen has only what I need to make a call:

- Candlestick chart with MACD underneath, with timeframe buttons (15m, 1h, 4h, 1D).

- Amount slider from zero to my spendable cash. Spendable means wallet balance minus the amount held back for fees and tax. Presets at 25 / 50 / 75 / 100%.

- Cost preview that updates as I move the slider: estimated fee, expected fill price, and what I actually end up with.

- Two buttons: Buy and Sell. If I have bought and not sold, the screen simply shows that I am holding.

- Position panel: what I hold, entry price, and profit or loss after fees.

- Favourites: a short list of coins I'm keeping an eye on, one tap to switch between them.

## 5. News and alerts

News comes in two parts, because that is how I think about it:

- Global news: macro and market-wide events such as Fed decisions, regulation, and major crypto headlines.

- Coin news: when I click a coin, I see news and upcoming events specific to that coin, including technical events coming in the next week or two.

Design rule: any interpretation ("the Fed is going to do X, which probably means Y") is shown as a one-line summary with a link to the source headline. Machine-generated interpretation can be confidently wrong, so I can always check it myself.

Price alerts: "tell me when ETH crosses X," tied to my favourites.

## 6. Built-in protection

These exist because the interface is designed to make trading effortless, and effortless trading needs safety rails.

- Limit orders by default to avoid slippage, with maker fees usually lower than taker fees. (Check Kraken's current fee schedule for my tier.)

- Automatic stop-loss on every buy, with the percentage set once in settings and placed with the order, so I never hold an unprotected position.

- Daily loss limit. If I'm down a set percentage on the day, the Buy button locks.

- Trade-only API keys. The Kraken keys have trading permission and never withdrawal permission, so a compromised app or machine cannot move my money out.

- Spendable-cash cap. The slider can never commit money set aside for fees and tax.

## 7. Record keeping

- Quiet trade log. Every trade is recorded automatically along with the chart state at the time. No effort from me.

- CSV export with cost basis to make tax time and accountant conversations far easier.

- Candidate log (later). If the app ever shows suggestions, it logs what it showed, what I chose, and what happened afterwards, so I can find out honestly whether my judgement or the machine's adds value.

## 8. What this is not

- Not an autonomous trading bot.

- Not a replacement for Kraken or Kraken Pro. It trades through Kraken Pro's APIs and does not hold custody of funds.

- Not a product for other people (for now). It is for my own trading. Offering personalised trade suggestions to others could bring investment-advice regulation, which would need proper legal advice first.

- Not a promise of profit. It removes friction and hassle. It does not create an edge by itself.

## 9. Build order

1. Chart, MACD, and favourites with live prices. The screen I will look at every day.

2. Practice mode: buy, sell, and the slider using pretend money, so I can get used to it with nothing at stake.

3. Connect to Kraken Pro via the API, reusing Jarvis's plumbing, and wire the buttons to real orders (with the protections from section 6 in place first).

4. News panel: global and per-coin feeds, starting with a simple version.

5. Alerts, history export, and polish.

A clickable mock-up of the main screen comes before any wiring, so I can see how it feels first.

## 10. How I'll know it's working

The tool test: is trading faster, calmer, and less hassle than doing it by hand? Do I stay within my own limits?

The honest test: is my trading actually profitable after fees? The cockpit makes this answerable, because everything is logged. Before judging, I'll write down in advance what counts as a pass, in the spirit of the 34/9/9 concept: how many trades, which measure (expectancy per trade net of fees, not win rate), and what threshold. That stops a lucky streak being mistaken for skill.

## 11. Risks to keep in view

- The edge is a hypothesis, not a given. Argus did not find a robust edge. The cockpit tests whether my discretionary judgement has one. If it doesn't, the tool just makes losing easier.

- Frictionless trading encourages overtrading. The daily loss limit and the trade log are the counterweights.

- Fees add up. Frequent small trades can be eaten alive by costs, so the cost preview matters.

- Start small. Practice mode first, then small real amounts, and only scale up if the results justify it.

I'm not a financial advisor, so treat the trading and regulatory points here as framing, not advice.

## 12. Open questions

- Crypto only, or equities later?

- What stop-loss percentage and daily loss limit feel right?

- How much of the wallet is held back for fees and tax, and is that a fixed percentage or a manual figure?

- Should the app ever suggest candidates, or stay purely a manual tool?

- Which news sources are worth feeding in?
