# Jobs to be done

**Trading Cockpit: Vision Document**

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

## 13. Jobs to be done

The common thread: the app replaces watching, calculating and admin, but never the decision.

### Staying in control of what I hold

1. Know where I stand. When I open the app, I want to see my spendable cash, what is currently in trades, and my profit after fees, so I don't have to do any sums.

2. Know what kind of market it is. I want a simple flag (going up, going down, or sideways) so I know whether to be bold or careful today.

3. Spot trouble before the stop-loss does. I want to be warned when something I hold is going wrong (momentum fading, MACD turning down, bad news, an unlock coming up) so I can choose to sell early.

4. Get out fast. If I don't like what I see, I want to sell one coin or everything quickly, with a confirmation step so I can't do it by accident.

### Finding and understanding new ideas

5. Find reasons to look at something new. I want a "What looks good today?" button that gives me a shortlist of coins where something has just happened (a MACD cross, a volume spike), each with the reason shown, so I only spend time on the interesting ones.

6. Judge one coin properly. When I click a coin, I want the chart, MACD and local data in one place so I can decide whether I like it.

7. Understand the news without reading everything. I want global news alongside, and coin-specific news inside the coin's row, including scheduled events such as token unlocks, so I know what is coming.

### Buying

8. Decide how much to commit. I want to slide an amount up to my spendable cash, never the money held back for fees and tax, so I never overcommit.

9. See what it will really cost. Before I click, I want the estimated fee, expected fill price, and what I will actually end up with, so there are no surprises.

10. Buy in one click. I want one Buy button that places a sensible order (a limit order by default, to avoid slippage) without me thinking about order types.

11. Be protected the moment I buy. I want my stop-loss placed automatically with the order, so I never hold an unprotected position.

12. Confirm it worked. I want to see the purchase land in my positions table straight away, with my entry price and profit after fees.

13. Redeploy after selling. When I have sold things and have cash again, I want to go straight to "What looks good today?" and then to buying, in one flow.

14. Be stopped from doing something daft. If I have hit my daily loss limit, or the amount is bigger than I am allowed, the app refuses before I buy, not after.

### Once, and underneath everything

15. Set it up once and trust it. I want to connect Kraken safely with trade-only keys, set my fee and tax reserve, stop-loss and loss limit, and practise with pretend money first.

16. Learn whether my own judgement makes money. Over time, I want to see how my decisions actually performed after fees. The quiet trade log answers this with no extra effort from me.

## 14. The journey

### First use (once)

1. Connect Kraken Pro with trade-only API keys (never withdrawal).

2. Set the fee and tax reserve, default stop-loss, and daily loss limit.

3. Pick my favourite coins.

4. Start in practice mode with pretend money.

5. Switch to real money, in small amounts, when I am comfortable.

### Everyday use

The app is a web page that can sit open all day, or be wrapped to look and behave like an app. The flow:

1. Open and glance. Wallet cash, money in trades, profit after fees, and the market mood flag.

2. Review what I hold. A table of positions, each with profit or loss and any warning flags. Decide hold or sell. If the mood is bad, "sell everything" (with confirmation).

3. Find new ideas. Press "What looks good today?" to get the shortlist, each coin showing why it is there.

4. Inspect. Click a coin for a small summary in the table, or open the full chart screen with candles, MACD and local data.

5. Check the news. Coin news expands inside the table row. Global news sits in a panel on the right.

6. Decide and act. Move the slider, check the cost preview, press Buy. The stop-loss goes on automatically. Close the tab.

## 15. The home screen

- Top strip: spendable cash, money currently in trades, profit after fees, and the market mood flag (up, down, sideways).

- Main table (left): my holdings and the favourites list, with profit or loss, warning flags, and a news button. Clicking news expands the row slightly to show local news for that coin.

- Right-hand panel: global news and how it might affect crypto.

- "What looks good today?" button: produces the shortlist of coins to look at.

- Coin click-through: a separate chart screen with candles, MACD, local data, the slider, and the Buy and Sell buttons.

- Sell everything: available, but always behind a confirmation step that shows the fees it would cost.

## 16. How "What looks good today?" behaves

- The button label stays as it is. It is a prompt for where to spend my attention, not a prediction.

- A deterministic engine (the same market conditions always give the same list) finds coins where something has just happened, for example a MACD cross, a volume spike, a break above recent highs, or momentum turning after a pullback.

- Every coin on the list shows the reason it is there, so I can glance at the trigger and decide whether it is worth my time.

- I choose which triggers count, using a short list of tick-boxes in settings, so the list reflects how I read charts.

- The list does not say a coin will go up. I make the judgement.

## 17. Coin news and token unlocks

Token unlocks (such as the ENA unlock) are scheduled events, so they can be tracked in advance rather than discovered afterwards. The coin news panel should show:

- The next unlock: date, size as a percentage of circulating supply, approximate dollar value, and who receives it. A small regular drip is very different from a large cliff.

- A countdown flag on coins I hold, shown next to profit and loss, such as "Unlock in 3 days".

- That coin's own history: its last few unlocks, with what the price did in the week before and the week after. This is built from real price data, so I can judge whether the coin tends to dip into unlocks or shrug them off.

- A caution tag on the shortlist: a coin with a MACD cross and a large unlock in two days shows both tags, so I see the whole picture.

As a general rule of thumb, large unlocks relative to circulating supply often see weakness build into the date, but what happens afterwards varies a lot. The app shows each coin's actual history rather than relying on a generic claim.

Data sources to investigate: unlock schedules from aggregators such as Tokenomist or CoinMarketCal, or directly from project tokenomics docs. Check which has a usable API before committing.
