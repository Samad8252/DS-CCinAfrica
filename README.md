# Climate Stress and Crop Production in Africa

**Data Science Final Project** | Abdulsamad Sulyman 

An end-to-end pipeline that links long-run temperature trends to agricultural performance across 15 major African cities, then forecasts city-level climate risk for 2030, 2040, and 2050. The goal is not to make causal claims. It is to integrate large, messy climate and crop datasets into one framework and flag regions where climate stress and agricultural underperformance increasingly coincide.

Full write-up with figures: [abdulsamadsulyman.com/dsproject](https://www.abdulsamadsulyman.com/dsproject)

---

## Data

Four raw datasets, roughly 41.6M rows in total:

| Dataset | Content | Raw size |
|---|---|---|
| 1 | Monthly city temperatures (1780 to 2010) | ~8.6M observations |
| 2 | Daily city temperatures (1995 onward) | ~2.9M records |
| 3 | Country-level crop production and exports | ~2.5M records |
| 4 | Daily weather (temperature, precipitation, wind) | ~27.6M rows |

Geographic and name filtering reduces this to about 575K analytically relevant records while preserving the long-run trends.

---

## Notebooks

Run in order.

**1. `Notebook1_Setup_Cleaning.ipynb`**
- Set directory paths (edit these before running)
- Load raw CSVs with a UTF-8 to Latin-1 encoding fallback
- Filter to the 15 target cities and their countries using accent-insensitive fuzzy matching
- Standardize date formats across monthly, daily, and annual data
- Remove invalid sentinel values (such as -99) without imputing
- Export `ProcessedDataset1-4.csv`

**2. `Notebook2_FeatureEngineering.ipynb`**
- Filter out city-years with incomplete seasonal coverage
- Compute 6-month rolling averages and linear warming trends per city (°F per decade)
- Compare crop production against a 3.5% annual expected growth baseline
- Correlate each city's warming rate with how far its crop production falls from expected growth
- Save per-city plots and summary charts

**3. `Notebook3_Modeling_Forecasting.ipynb`**
- Aggregate temperature data to the decade level (mean, max, min, std, within-decade trend, latitude, longitude, distance from equator)
- Train a Random Forest and Gradient Boosting ensemble
- Project temperature for 2030, 2040, and 2050 under conservative (+0.2°C/decade), moderate (+0.3°C/decade), and high (+0.4°C/decade) warming scenarios
- Compute a 0 to 100 climate risk score from absolute temperature, warming magnitude, and variability, binned into Low, Moderate, High, and Extreme
- Export forecast maps, scenario comparisons, and a 2050 high-risk summary table

---

## Results

- **144 climate risk scenarios** generated across cities, forecast years, and warming pathways
- Ranked risk tables and spatial vulnerability maps highlighting the highest-risk cities in 2050
- Per-city crop production deviation from expected growth, plus a cross-city summary
- Warming rates per decade for each city over 1780 to 2010 and 1995 to 2010

Figures are saved to `Plots - Climate`, `Plots - Crop Yield`, `Plots - Correlation`, and `Plots - ML_Forecasts`.

**Limitations.** Forecasts are scenario-driven: future warming rates are assumed inputs, not learned from the data. The crop growth baseline is a fixed 3.5% per year, so deviations reflect many factors beyond climate (technology, policy, land use). Results show where signals coincide, not what causes them.

---

## Path Note (Read Before Running)

File paths in the notebooks are machine-specific. Update the directory variables in the first code cells of Notebook 1 (and the load and save paths in Notebooks 2 and 3) to match your system. Downstream notebooks read the files Notebook 1 creates.

---

## Requirements

- Python 3.9+
- Jupyter Notebook or JupyterLab
- `pandas`, `numpy`, `scipy`, `scikit-learn`, `matplotlib`, `seaborn`, `tqdm`, `rapidfuzz`, `unidecode`, `adjustText`

```bash
pip install pandas numpy scipy scikit-learn matplotlib seaborn tqdm rapidfuzz unidecode adjustText
```

---

## Contact

Abdulsamad Sulyman | [LinkedIn](https://www.linkedin.com/in/asuly/)
