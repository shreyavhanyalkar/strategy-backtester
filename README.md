My name is Shreya Vhanyalkar. I have completed an assignment called Strategy Backtester Engine. It is a backend task. Run all the code and go into "view data" to view all the visual representation.

Code Explanation:
This project builds a Strategy Backtester that simulates how trading strategies would have performed in the past using real data from Binance.

1. Fetching Real Market Data

fetch_binance_data()

This function connects to Binance API.
It downloads the last 5000 one-minute candle data (open, high, low, close, volume) for a crypto coin (like BTCUSDT).
The data is stored in a DataFrame — which is like a table in Python.

2. MACD-EMA Strategy

apply_macd_strategy()

MACD (Moving Average Convergence Divergence) is a trading indicator.
The strategy buys when MACD line crosses above its own EMA (signals uptrend).
It sells when MACD line crosses below its EMA (signals downtrend).
Signals are marked in a new signal column in the data.

3. RSI + EMA(21) Strategy

apply_rsi_ema_strategy()

RSI (Relative Strength Index) checks if the asset is oversold or overbought.
EMA(21) is a smooth average of prices over 21 minutes.
The strategy buys when:

RSI goes above 30 (coming out of oversold)

AND price is above EMA(21) (uptrend)

It sells when:

RSI drops below 70

OR price falls below EMA(21)

4. Backtesting the Strategy

backtest_strategy()

This function checks every row (minute) in the data:
If there's a Buy Signal, it enters a trade.
When a Sell Signal appears, it exits the trade.
It records:

Entry Time

Entry Price

Exit Time

Exit Price

Strategy Used

Profit/Loss

Win or Loss

5. Putting It All Together

if __name__ == "__main__":
The script:

Gets Binance data

Applies MACD and RSI-EMA strategies

Backtests both and collects results

Combines all trades into one file


Prints the trades and saves them in a file:
strategy_backtest_results.csv


Example Output:
Entry Time	Entry Price	Exit Time	Exit Price	Strategy	PnL	Status
2025-06-02 10:00	27890.50	2025-06-02 12:15	28100.10	MACD-EMA	+209.60	Win