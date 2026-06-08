<div align="center">

# Bitcoin Market Sentiment vs Trader Performance Analysis

**Uncovering the statistical relationship between the crypto Fear & Greed Index and real-world trading profitability using large-scale time-series data.**

[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://www.python.org/downloads/)
[![Pandas](https://img.shields.io/badge/Pandas-Data_Analysis-150458.svg?logo=pandas)](https://pandas.pydata.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626.svg?logo=jupyter)](https://jupyter.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

</div>

---

## 📸 Visuals

![Demo](./assets/demo.gif)
*(Placeholder: A brief visualization of the analysis pipeline or generated plots)*

## 🔗 Live Links

- **[Live Notebook Viewer](#)** *(Replace with nbviewer or deepnote link)*
- **[Presentation Deck](./Bitcoin%20Market%20Sentiment%20vs%20Trader%20Performance%20Analysis.pptx)**

---

## ✨ Features

- **Automated Time-Series Alignment**: Intelligently synchronizes sparse historical market sentiment data with high-frequency, precision-timestamped trade executions.
- **Profitability Categorization**: Analyzes closed PnL metrics to categorize trades by win/loss rates under varying sentiment classifications (e.g., Extreme Fear vs. Extreme Greed).
- **Extensive Data Cleaning**: Robust data imputation and cleansing pipelines to handle missing sentiment rows, disparate date formats, and corrupted metrics.
- **Visual Analytics**: Generates interpretable Matplotlib visualizations correlating market emotion metrics with average trade profit and trade frequency.

## 💻 Tech Stack

- **Language:** Python
- **Data Manipulation:** Pandas, NumPy
- **Data Visualization:** Matplotlib
- **Environment:** Jupyter Notebook, Google Colab

---

## 🚀 Installation & Setup

<details>
<summary><b>Click to expand setup instructions</b></summary>

### Prerequisites
- Python 3.9+
- Jupyter Notebook or JupyterLab

### Steps

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/bitcoin-sentiment-analysis.git
   cd bitcoin-sentiment-analysis
   ```

2. **Set up a virtual environment (Recommended):**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. **Install dependencies:**
   ```bash
   pip install pandas matplotlib jupyter
   ```

4. **Environment Variables:**
   Create a `.env` file from the example template to configure data paths (if applicable).
   ```bash
   cp .env.example .env
   ```

5. **Run the Notebook:**
   ```bash
   jupyter notebook "Untitled1.ipynb"
   ```
</details>

---

## 🏗️ Architecture / Data Flow

The core logic of the analysis pipeline is structured sequentially:

1. **Ingestion**: Raw execution data (`historical_data.csv`) and sentiment indices (`fear_greed_index.csv`) are ingested into Pandas DataFrames.
2. **Transformation**: Timestamps are normalized to unified `DateTime` objects, stripping timezone discrepancies.
3. **Merging**: Instead of strict inner joins, an **As-Of Merge** (`pd.merge_asof`) strategy is utilized to map each trade to the most relevant sentiment index based on chronological proximity.
4. **Aggregation**: Trades are grouped by `classification` (e.g., Greed, Fear) to compute statistical summaries including average profit and win probabilities.
5. **Visualization**: Processed distributions are rendered as bar charts to visually convey the sentiment-to-performance correlation.

---

## 🧠 Technical Highlights & Learnings

**Challenge: Asynchronous Time-Series Data**
The most significant technical hurdle was combining high-frequency trade data (with timestamps down to the minute) with daily/sparse market sentiment snapshots. A standard SQL-style `JOIN` would result in massive data loss due to non-matching keys.

**Solution:**
I implemented Pandas' `merge_asof` function, pre-sorting both datasets chronologically. This algorithm performs a rolling directional join, matching each trade execution with the *nearest* preceding sentiment value.

**Learning Outcome:**
This approach not only preserved 100% of the 211,224 rows of trade data but also optimized memory usage and execution time compared to a naive cross-join or `.apply()` mapping. It demonstrated the importance of leveraging optimized, vectorized operations for time-series analysis over custom loops.

---

## 📫 Contact

Let's connect! I'm actively looking for opportunities where I can contribute to impactful data and engineering challenges.

- **LinkedIn**: [linkedin.com/in/yourprofile](#)
- **Portfolio**: [yourportfolio.com](#)
- **Email**: [your.email@example.com](mailto:your.email@example.com)