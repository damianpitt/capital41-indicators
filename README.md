# Capital41 Indicators

A collection of PineScript v6 indicators and strategies for TradingView by CAPITAL41, covering trend, momentum, volatility, market structure, session analysis, and crypto-specific tools. Mainly designed for 30m and 4h timeframes on BTC and US equities.

Every script is fully standalone: paste into Pine Editor, save, and add to chart. No external dependencies.


## Indicators


### Market Structure

- **Liquidity Sweep** 
  Detects stop-hunt sweeps beyond swing highs/lows with volume confirmation. Tracks consecutive sweeps at similar levels for higher-probability setups.

- **Liquidity Void Imbalance Map** 
  Identifies Fair Value Gaps (FVGs) on LTF and optional HTF. Merges overlapping zones, tracks fill percentage and age, computes urgency rankings, and highlights breaker events.

- **Structure Swings v3** 
  Marks swing highs/lows via pivot detection and Break of Structure (BOS). Draws persistent level lines that update only on new swings.

- **Order Block Detector v2** 
  Finds institutional demand/supply zones — the last opposing candle before an impulse move. Tracks mitigation, age-fades boxes, and prevents duplicate zones.
  
- **Divergence Detector v2** 
  Detects regular and hidden divergences on both RSI and Williams %R. Draws divergence lines on price, scores conviction (DIV+ when both oscillators agree).


### Confluence & Signals

- **Confluence Core** 
  Combines MA trend, RSI, Williams %R, and Liquidity Sweep into a single signal with three strictness modes (Strict / Standard / Loose).
  
- **Fusion Scalp v3** 
  Four-condition confluence: EMA trend + RSI + Williams %R + ATR/Volume expansion.
  
- **Fusion Oscillator v3** 
  Companion 0-100 oscillator for the Fusion Scalp system. Maps all four conditions into a composite score.
  
- **Capital41 Duo** 
  RSI and Williams %R combined into a simple starting signal, with reversal checks and normalization. Background shifts when both oscillators agree on oversold or overbought.
	
- **Capital41 Duo Oscillator** 
  Companion 0-100 oscillator for the Duo.


### Trend & Regime

- **Regime Matrix v3** 
  Classifies bars into Trend, Expansion, Compression, or Mean Reversion using Hurst exponent, ADX slope, and realized volatility. Auto-adapts EMA length and ATR stop width per regime.

- **ADX Filter v3** 
  ADX with DI+ and DI- directional lines, fill shading, strong trend threshold, status badge, and alerts.

- **Williams Flow v2** 
  HTF Williams %R regime filter with current-TF flow signals. User-configurable line color for dark/light theme compatibility.


### Volatility & Levels

- **ATR Volatility Bands v2**
  ATR-based upper/lower bands around a moving average with optional recent-range box and volatility expansion highlighting.
  
- **PDH/PDL Levels v3** 
  Previous Day/Week/Month High/Low with midpoints, right-edge labels, level fills, touch/breakout detection, and proximity badge.
  
- **Session VWAP v2** 
  Manual intraday VWAP with standard deviation bands that resets each session. Configurable session times and timezone.


### Session & Calendar

- **Session Flow v2** 
  Draws color-coded session boxes for Asia, London, and New York. Tracks session highs/lows, open lines, breakout markers, and range comparisons.
  
- **Opening Drive Playbook v2** 
  Builds a dynamic Opening Drive range from the first 30/60 minutes. Computes drive pace, relative volume, adaptive continuation/fade triggers, gap size, and pullback depth.
  
- **Key Calendar** 
  Marks recurring market-structure dates: month/quarter/year opens, OPEX, earnings kickoff, Russell rebalance, and two custom date slots.


### Crypto-Specific

- **Crypto Perp Stress** 
  Detects stress in crypto perpetual markets using the basis (spot vs perp), open interest impulse, and liquidation "wick" behavior. Includes weekend sensitivity adjustments.


### Strategies (Backtestable)

- **C41 Core Strategy v2** 
  MA + RSI + Williams %R strategy with entry-locked ATR stop-loss and take-profit. Set to a realistic 0.075% commission.
  
- **C41 Oscillator** 
  Companion 0-100 oscillator for the C41 Core Strategy.
  
- **Fusion Core Strategy v3**
  Converts the Fusion system into a backtestable strategy with entry-locked ATR TP/SL that doesn't shift bar-to-bar.


## Example Charts

Capital41 Duo applied across equities, crypto, FX, indices, and commodities:

| | |
|---|---|
| ![BTC](Capital41_Duo/Example%20Charts/BTC%202026-04-20.png) | ![Nasdaq 100](Capital41_Duo/Example%20Charts/Nasdaq%20100%202026-04-23.png) |
| **BTC** — crypto | **Nasdaq 100** — index |
| ![Gold CFD](Capital41_Duo/Example%20Charts/Gold%20CFD%202026-04-10.png) | ![TSLA](Capital41_Duo/Example%20Charts/TSLA%202026-04-16.png) |
| **Gold CFD** — commodity | **TSLA** — equity |

Full set in [`Capital41_Duo/Example Charts/`](Capital41_Duo/Example%20Charts) — AMZN, BTC, CHF/USD, Copper CFD, ETH, Gold CFD, Nasdaq 100, Nikkei 225, RACE.MI, Silver, TSLA, USD/AUD.


## Quick Start

1. Open [TradingView](https://www.tradingview.com/) and go to **Pine Editor**.
2. Copy the contents of any `.pine` file from this repo.
3. Paste into the editor, click **Save**, then **Add to Chart**.
4. Start with a 30m chart on BTC or any US equity.


## Design Principles

- **PineScript v6** — all scripts use the latest version as of 2026.
- **Non-repainting** — every marker and alert is gated by `barstate.isconfirmed`, or derives from pivots that are confirmed on both sides. Nothing prints mid-bar and then disappears.
- **Standalone** — every script works independently with no imports or dependencies.
- **Consistent conventions** — lime/red color scheme, "L"/"S" signal labels, status badges, and `"<Script>: <event> on {{ticker}} ({{interval}})"` alert messages across the suite.

## Suite Workflow

```
Duo / Duo Oscillator  -   quick momentum read, entry bias
Divergence Detector   -   trend exhaustion signal
Order Block           -   institutional entry zone
Liquidity Sweep       -   stop-hunt confirms the zone
Liquidity Void Map    -   imbalance target for the move
Structure Swings      -   BOS confirms structure shift
Regime Matrix         -   adapts risk to market state
```

## License

[MIT](LICENSE) - free to use, modify, and distribute with attribution.

Copyright (c) 2026 CAPITAL41
