# Bitcoin Market Sentiment vs. Trader Performance Analysis

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg?style=flat&logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-2.0+-darkblue.svg?style=flat&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-orange.svg?style=flat)](https://matplotlib.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg?style=flat&logo=jupyter&logoColor=white)](https://jupyter.org/)

An empirical data analysis project exploring the correlation between Bitcoin market sentiment (quantified by the **Crypto Fear & Greed Index**) and actual trader performance/behavior (derived from execution logs).

---

## 📌 Project Overview

Does market sentiment drive trader profitability, or do traders perform better when defying sentiment extremes? This project merges granular trade execution data with historical Crypto Fear & Greed Index classifications to answer these questions. 

By aligning daily sentiment indices with timestamped trade executions, we analyze:
*   **Trading Activity Volume**: How trade frequency changes during Extreme Fear vs. Extreme Greed.
*   **Profitability Analysis (PnL)**: The average Profit & Loss per trade grouped by market sentiment.
*   **Win Rate vs. Sentiment**: Do traders exhibit higher win/loss ratios under specific emotional states of the market?

---

## 🛠️ Tech Stack & Libraries

*   **Language**: Python 3.8+
*   **Data Manipulation**: `pandas`
*   **Data Visualization**: `matplotlib`
*   **Workspace**: Jupyter Notebook / Google Colab

---

## 📊 Dataset Structure

The analysis combines two core datasets:

### 1. Trader Execution Data (`historical_data (1).csv`)
Contains historical trading logs with granular execution details:
*   `Account`: Unique identifier for the trader's account.
*   `Coin`: Traded asset (BTC, ETH, etc.).
*   `Execution Price`: Price at which the trade was executed.
*   `Size Tokens` / `Size USD`: Size of the position.
*   `Side` / `Direction`: Buy/Sell (Long/Short) details.
*   `Closed PnL`: The realized Profit and Loss of the trade.
*   `Timestamp IST`: Granular timestamp of the trade execution.

### 2. Market Sentiment Data (`fear_greed_index (1).csv`)
Contains daily scores from the Crypto Fear & Greed Index:
*   `date`: Date of the index record.
*   `value`: Numeric sentiment score (0 - 100).
*   `classification`: Classification label (`Extreme Fear`, `Fear`, `Neutral`, `Greed`, `Extreme Greed`).

---

## ⚙️ Methodology & Pipeline

1.  **Date-Time Alignment**:
    *   Traders execute positions at granular timestamps (seconds/minutes), whereas the sentiment index is published daily.
    *   To merge them accurately, timestamps are parsed, sorted, and matched using Pandas' high-performance `pd.merge_asof()` (nearest-match method) to pair each trade with the closest sentiment index reading.
2.  **Data Cleaning**:
    *   Converting types, sorting time-series data, and dropping records outside the overlapping timeline.
    *   Mapping PnL values to categorical outcomes (`Win` / `Loss`).
3.  **Statistical Aggregations**:
    *   Grouping trades by their corresponding sentiment classification.
    *   Computing descriptive statistics for trade frequency, mean profit, and win/loss ratio.
4.  **Data Visualization**:
    *   Generating comparative bar charts and distribution plots using `matplotlib`.

---

## 📂 Repository Contents

*   📂 **`Bitcoin_Sentiment_vs_Trader_Performance_Analysis.ipynb`**: The main Jupyter Notebook executing the data loading, preprocessing, cleaning, time-series merging (`merge_asof`), statistical grouping, and chart generation.
*   📂 **`Bitcoin Market Sentiment vs Trader Performance Analysis.pptx`**: A comprehensive PowerPoint presentation summarizing the methodology, strategic insights, visualization highlights, and final trading takeaways.

---

## 🚀 How to Run the Analysis

1.  **Clone the Repository**:
    ```bash
    git clone https://github.com/oindrilaverse/Data-Analysis-Bitcoin.git
    cd Data-Analysis-Bitcoin
    ```

2.  **Install Dependencies**:
    Make sure you have Python installed, then install the required libraries:
    ```bash
    pip install pandas matplotlib notebook
    ```

3.  **Place the Datasets**:
    Ensure the data files `historical_data (1).csv` and `fear_greed_index (1).csv` are present in the directory or update the paths in the notebook.

4.  **Run the Notebook**:
    ```bash
    jupyter notebook Bitcoin_Sentiment_vs_Trader_Performance_Analysis.ipynb
    ```
