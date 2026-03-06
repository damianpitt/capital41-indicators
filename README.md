# Capital41 Indicators

A collection of PineScript v6 indicators and strategies for TradingView by CAPITAL41, covering trend, momentum, volatility, market structure, session analysis, and crypto-specific tools. Mainly designed for 30m and 4h timeframes on BTC and US equities.

Every script is fully standalone: paste into Pine Editor, save, and add to chart. No external dependencies.


## Indicators


### Market Structure

- **Liquidity Sweep** 
  Detects stop-hunt sweeps beyond swing highs/lows with volume confirmation. Tracks consecutive sweeps at similar levels for higher-probability setups.

- **Liquidity Void Imbalance Map** 
  Identifies Fair Value Gaps (FVGs) on LTF and optional HTF. Merges overlapping zones, tracks fill percentage and age, computes urgency rankings, and highlights breaker events.

- **Structure Swings v2** 
  Marks swing highs/lows via pivot detection and Break of Structure (BOS). Draws persistent level lines that update only on new swings.

- **Order Block Detector** 
  Finds institutional demand/supply zones — the last opposing candle before an impulse move. Tracks mitigation, age-fades boxes, and prevents duplicate zones.
  
- **Divergence Detector** 
  Detects regular and hidden divergences on both RSI and Williams %R. Draws divergence lines on price, scores conviction (DIV+ when both oscillators agree).


### Confluence & Signals

- **Confluence Core** 
  Combines MA trend, RSI, Williams %R, and Liquidity Sweep into a single signal with three strictness modes (Strict / Standard / Loose).
  
- **Fusion Scalp v2** 
  Four-condition confluence: EMA trend + RSI + Williams %R + ATR/Volume expansion.
  
- **Fusion Oscillator** 
  Companion 0-100 oscillator for the Fusion Scalp system. Maps all four conditions into a composite score.


### Trend & Regime

- **Regime Matrix** 
  Classifies bars into Trend, Expansion, Compression, or Mean Reversion using Hurst exponent, ADX slope, and realized volatility. Auto-adapts EMA length and ATR stop width per regime.

- **ADX Filter v2** 
  ADX with DI+ and DI- directional lines, fill shading, strong trend threshold, status badge, and alerts.

- **Williams Flow v2** 
  HTF Williams %R regime filter with current-TF flow signals. User-configurable line color for dark/light theme compatibility.


### Volatility & Levels

- **ATR Volatility Bands**
  ATR-based upper/lower bands around a moving average with optional recent-range box and volatility expansion highlighting.
  
- **PDH/PDL Levels v2** 
  Previous Day/Week/Month High/Low with midpoints, right-edge labels, level fills, touch/breakout detection, and proximity badge.
  
- **Session VWAP** 
  Manual intraday VWAP with standard deviation bands that resets each session. Configurable session times and timezone.


### Session & Calendar

- **Session Flow** 
  Draws color-coded session boxes for Asia, London, and New York. Tracks session highs/lows, open lines, breakout markers, and range comparisons.
  
- **Opening Drive Playbook** 
  Builds a dynamic Opening Drive range from the first 30/60 minutes. Computes drive pace, relative volume, adaptive continuation/fade triggers, gap size, and pullback depth.
  
- **Key Calendar** 
  Marks recurring market-structure dates: month/quarter/year opens, OPEX, earnings kickoff, Russell rebalance, and two custom date slots.


### Crypto-Specific

- **Crypto Perp Stress** 
  Detects stress in crypto perpetual markets using the basis (spot vs perp), open interest impulse, and liquidation "wick" behavior. Includes weekend sensitivity adjustments.


### Strategies (Backtestable)

- **C41 Core Strategy v2** 
  MA + RSI + Williams %R strategy with entry-locked ATR stop-loss and take-profit. Realistic set a 0.075% commission.
  
- **C41 Oscillator** 
  Companion 0-100 oscillator for the C41 Core Strategy.
  
- **Fusion Core Strategy v2**
  Converts the Fusion system into a backtestable strategy with entry-locked ATR TP/SL that doesn't shift bar-to-bar.


## Quick Start

1. Open [TradingView](https://www.tradingview.com/) and go to **Pine Editor**.
2. Copy the contents of any `.pine` file from this repo.
3. Paste into the editor, click **Save**, then **Add to Chart**.
4. Start with a 30m chart on BTC or any US equity.


## Design Principles

- **PineScript v6** — all scripts use the latest version as of 2026.
- **Non-repainting** - signals use `barstate.isconfirmed` and confirmed pivots.
- **Standalone** — every script works independently with no imports or dependencies.
- **Consistent conventions** — lime/red color scheme, "L"/"S" signal labels, status badges, and alert conditions across the suite.

## Suite Workflow

```
Divergence Detector  :   trend exhaustion signal
Order Block          :   institutional entry zone
Liquidity Sweep      :   stop-hunt confirms the zone
Liquidity Void Map   :   imbalance target for the move
Structure Swings     :   BOS confirms structure shift
Regime Matrix        :   adapts risk to market state
```

## License

[MIT](LICENSE) - free to use, modify, and distribute with attribution.

Copyright (c) 2026 Capital41
