# Ea-BbMaxRsi-v1

### Status
The EA has already been further developed, but there will be no further updates here, this one here works well enough as a example working EA.

## Description
The "Wisetime_BB-MAX-RSI-CE" EA for MetaTrader 5 is a cut down version of my EA, serving as a solid foundation for developing your own trading bot. It combines Bollinger Bands, Moving Average Crossover, and RSI strategies with customizable risk management and trading settings. This adaptable and efficient tool is designed to cater to various market scenarios and trading styles.

### Features
- **Multiple Strategies:** Offers Bollinger Bands, Moving Average Crossover, and RSI strategies with customizable settings.
- **Trade Directionality:** Allows trend following, trend reversal, and bi-directional trades.
- **Risk Management:** Enables setting risk levels, stop loss, and take profit to protect capital.
- **Custom Time Frames:** Supports various time frames from 30 minutes to 12 hours for strategy execution.
- **Day-of-Week Control:** Permits trading on selected weekdays, optimizing trading strategy.
- **Equity Protection:** Stops trading if losses exceed a specified percentage, safeguarding account equity.
- **Signal Processing:** Combines multiple indicators for robust buy or sell decisions.
- **Spread Management:** Executes trades considering spread conditions to ensure favorable entry.
- **Magic Number Use:** Identifies trades with a unique number, distinguishing EA-managed trades.

### Preview
- The external inputs...
```
// External Inputs
input string ___Ea_Settings___ = "--= EA Settings - (Settings For The Ea) =--";
input int MagicNumber = 12345; 
input double LossPercentOff = 25.0;
input string ___Timer_Settings___ = "--= Timer Settings - (Settings For Timings) =--";
input double SpreadPercent = 10.0;
input bool TradeOnMonday = true;
input bool TradeOnTuesday = true;
input bool TradeOnWednesday = true;
input bool TradeOnThursday = true;
input bool TradeOnFriday = true;
input string ___General_Strategy___ = "--= General Strategy (Strategy Switches) =--";
input StrategySelection StrategyUsed = BB_RSI_MAX_STRATEGY;
input OrderDirections Order_Direction = BUY_SELL;
input int Trade_Slots = 2;
input double RiskPercent = 2.0;
input double TakeProfit = 50;
input double StopLoss = 50;
input string ___Bollinger_Bands___ = "--= Bollinger Bands (Strategy One) =--";
input Signal_Bars_Valid_Long BB_BarsValid = EIGHT__BARS;
input CustomTimeFramesStrategy BB_TimeFrame = H1_TIME;
input Trade_Direction BB_Direction = FOLLOW_TREND;
input double BB_Deviation = 2.0;
input int BB_Period = 20;
input string ___Moving_Average_Crossover___ = "--= Moving Average Crossover (Strategy Two) =--";
input Signal_Bars_Valid_Long MAX_BarsValid = EIGHT__BARS;
input CustomTimeFramesStrategy MAX_TimeFrame = H1_TIME;
input Trade_Direction MAX_TrendFollowing = FOLLOW_TREND; 
input int FastMA_Period = 9;
input int SlowMA_Period = 21;
input string ___Relative_Strength_Index___ = "--= Relative Strength Index (Strategy Three) =--";
input Signal_Bars_Valid_Short RSI_BarsValid = ONE_BAR;
input CustomTimeFramesStrategy RSI_TimeFrame = H1_TIME;
input Trade_Direction RSI_Direction = FOLLOW_TREND;
input int RSI_Period = 14;
input double RSI_Buy_Level = 30.0;
input double RSI_Sell_Level = 70.0;
```

## Usage
- Do not use it, you will loose money, unless...
1. You know what you are doing.
2. You are not trading money, that you do not mind loosing.
3. You have somehow upgraded the code, to make it more effective.
4. You have done backtesing on it.
5. You have done forward backtest on demo account.
- All that said...
1. Copy the Ea to your "MQL5\Experts" folder.
2. Load the Settings file. 
3. Its not great, but the loss-shutdown input will produce better quality results with less losses, you could put it high for backtesting, then loosen it up later.
4. Setup the other parts of the backtest, note its designed for between a M30-H12 timeframe. 
5. Run genetic backtest. 

### Notes
- To avoid market manipulation you should use a TimeFrame over M5, but, I would use at least M15, to remove such randomness.
- To gain consistent results, I would advise backtesting for 4 years of data, therein, you would probably want your TimeFrame to then become M30 or H1, for speed.
- I do notice that doing a backtest for short periods of history with a high takeprofit will definately result in non-reproducable results.

## Disclaimer
This software is subject to the terms in License.Txt, covering usage, distribution, and modifications. For full details on your rights and obligations, refer to License.Txt.
