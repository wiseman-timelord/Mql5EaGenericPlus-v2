# Mql5EaGenericPlus-v2

### Status
The Current blueprint for creating a EA with a SMMA 100 DayFilter confirmation. Feel free to download this project, and if you can make a trader better than the traders I have made for it, then also feel free to, fork and upload.

## Description
The "BB-MAX-RSI" EA Version 1 for MetaTrader 5, is a cut down version of the EA I have personally developed, serving as a solid foundation for developing your own trading bot. It has placeholder parts in in, "Strategy Manager" and "Execute Order", as well as a dummy function representing calculations required for main strategy. Gpt4 can be instructed to inspect the script, and then implement any combinations of main trading strategy, then fix the leftover issues. 

### Features
- **Descriptive Placeholder Parts:** Implement your own choice of strategy with customizable settings.
- **All other required code:** The script is complete otherwise.
- **Custom Enums**: Custom Enums for impressive reduction in calculations required during backtesting.  
- **Reduced Calculations**: Use of NewBar enables less intensive calculations not be done every tick. 

### Preview
- The Descriptive Overview of the Script...
```
// Script: BaseStrategy_Template
#property copyright "Your Copyright"
#property link      "https://www.mql5.com"
#property strict

// MT5 Includes
#include <Trade\Trade.mqh>
#include <Indicators\Indicators.mqh>

// Custom Enums
enum CustomBarsNumber { /* Your enums here */ };
enum StrategyTimeframe { /* Your enums here */ };
enum OrderDirections { /* Your enums here */ };
enum TradeDirection { /* Your enums here */ };
enum Signal_Filter_Type { /* Your enums here */ };
enum Custom_Dayfilter_Config { /* Your enums here */ };

// External Inputs
input string _EA_Settings_ = "--= EA Settings =--";
// Define your EA settings here...

// MT5 Classes
CTrade trade;

// Global Variables
// Define your global variables here...

// Function OnInit
int OnInit() {
    // Initialization code here...
    return INIT_SUCCEEDED;
}

// Function OnTick
void OnTick() {
    // Main trading logic here...
}

// Placeholder Strategy Manager Function
void StrategyManager() {
    // Define your strategy management logic here...
    // For example, evaluate conditions for a trading signal:
    bool signalBuy = false;
    bool signalSell = false;

    // Dummy conditions for buy or sell signals
    if (/* condition for a buy signal */) {
        signalBuy = true;
    } 
    if (/* condition for a sell signal */) {
        signalSell = true;
    }

    // Execute trade based on the evaluated signal
    if(signalBuy) {
        ExecuteOrder(DIRECTION_BUY);
    } else if(signalSell) {
        ExecuteOrder(DIRECTION_SELL);
    }
}

// Function to Update Strategy Indicators or Conditions
void UpdateStrategyConditions() {
    // Update any conditions or indicators needed for your strategy
}

// Function ExecuteOrder
void ExecuteOrder(TradeDirection direction) {
    // Execution logic here...
}

// Other Utility Functions as needed...
// For example, CalculateSLandTP, CheckShutdownCriteria, etc.

// Function OnDeinit
void OnDeinit(const int reason) {
    // Cleanup code here...
}
```
- External Inputs...
```
string _EA_Settings_ = "--= EA Settings - ( EA/Backtest Settings ) =--";
int MagicNumber = 12345; // Unique Identification of Chart
double LossPercentOff = 20.0; // % Loss to Shutdown EA
double DrawdownPercentOff = 33.0; // % Drawdown to Shutdown EA
string _Trade_Restrictions_ = "--= Restrictions Section - ( Settings For Trading ) =--";
CustomBarsNumber Min_Order_Bars = EIGHT_BARS; // Number of Bars per Order
double MaxSpreadAvePipMulti = 2.0; // Max Spread Average Pip Multiplier
int Trade_Slots = 2; // Maximum Orders across All Charts.
Custom_Dayfilter_Config Dayfilter_Days = MIDDLE_WEEK; // Set the default day filter
string _Strategy_Configuration_ = "--= Strategy Section ( Strategy Settings ) =--";
StrategyTimeframe Strategies_Timeframe = H3_TIME; // TimeFrame for IchiMoku
OrderDirections Order_Direction = BUY_SELL; // Direction of Orders
double RiskRewardRatio = 1.5; // TP in Ratio to SL
double MaxRiskPercent = 7.5; // Maximum Risk in Percent
string _Signal_Confirmation_ = "--= Signal Restriction  ( Loss Prevention ) =--";
Signal_Filter_Type Signal_Filter = NO_FILTER; // Choose your filter type
int Smma_Period = 100; // Smma Period (Default = 100)
```

## Requirements
- MetaTrader 5.
- A demo account.
- A lot of time.
- Algo-Trading Experience.

### Usage
- Its not possible to use this script directly as an EA, you need to implement the main strategy, but otherwise.

### Notes
- The number of bars thing, is to coordinate signals between indicators, there are 2 enums for this, long and short, same with timeframes I think.
- To avoid market manipulation you should use a TimeFrame over M5, but, I would use at least M15, to remove such randomness.
- To gain consistent results, I would advise backtesting for 4 years of data, therein, you would probably want your TimeFrame to then become M30 or H1, for speed.
- I do notice that doing a backtest for short periods of history with a high takeprofit will definately result in non-reproducable results.
- If you add more than 3 strategies, it starts to become a massive number of calculations involved, also GPT context suffers.
- GPT: "Considering the complexity and features of your EA, a base price could be in the $50 to $100 range"

## Disclaimer
This software is subject to the terms in License.Txt, covering usage, distribution, and modifications. For full details on your rights and obligations, refer to License.Txt.
