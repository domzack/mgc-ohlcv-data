# MGC Micro Gold Futures - Historical OHLCV Data

This repository contains historical OHLCV (Open, High, Low, Close, Volume) candlestick data for **Micro Gold Futures (MGC)** traded on CME (Chicago Mercantile Exchange).

## About This Data

- **Asset**: MGC - Micro Gold Futures
- **Exchange**: CME (Chicago Mercantile Exchange)
- **Contract Size**: 10 troy ounces of gold
- **Data Source**: Databento API

## Data Structure

Each CSV file contains one trading day of 1-minute OHLCV candles:

| Column | Description |
|--------|-------------|
| timestamp | Candle timestamp (YYYY-MM-DD HH:MM:SS) |
| open | Opening price |
| high | Highest price |
| low | Lowest price |
| close | Closing price |
| volume | Trading volume |

## File Naming

Files are named following the pattern: `ohlcv_MGC_YYYY-MM-DD.csv`

Example: `ohlcv_MGC_2023-01-02.csv` contains January 2nd, 2023 data.

## Date Range

Data available from: **2023-01-02** to **2026-03-23**

## Split do JSON grande por data

Para quebrar um arquivo NDJSON grande em arquivos menores por data (`hd.ts_event`), use:

```bash
python split_ohlcv_by_date.py glbx-mdp3-20230101-20260323.ohlcv-1m.json data/by-date
```

O script gera arquivos no formato `ohlcv-YYYY-MM-DD.jsonl`.

Se quiser sobrescrever arquivos já existentes:

```bash
python split_ohlcv_by_date.py glbx-mdp3-20230101-20260323.ohlcv-1m.json data/by-date --overwrite
```

## Contract Rollover Handling

This dataset uses a smart contract rollover strategy:
- Uses a 10-day moving average of volume to determine the most liquid contract
- Automatically switches to the new contract when it becomes more liquid
- This ensures continuous, gap-free price series

## Disclaimer

This data is provided for educational and informational purposes only. Not financial advice.