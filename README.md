# Giki-bootcamp-project
Solar Energy Forecasting

# Solar Energy Forecasting: PV Generation & Load Prediction

Kaggle competition project to predict **PV Generation** and **Load Consumption** at 10‑minute intervals for a 1–4 hour look‑ahead, and compute **efficiency = generation ÷ consumption**.

This repository is structured so a judge can **clone and run** it on a fresh machine without manual tweaks.

1. **Create & activate env**
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # on Windows: .venv\Scripts\activate
   pip install -r requirements.txt
   ```

2. **Put data in** `data/`:
   - `train_data.csv`, `test_data_masked.csv`, `systems_new.csv`, `sample_submission.csv`

3. **Run ARIMA baseline** (single command):
   ```bash
   python -m src.solar_forecast.arima_baseline      --train data/train_data.csv      --test data/test_data_masked.csv      --sample data/sample_submission.csv      --out submission.csv
   ```

4. **Output**: `submission.csv` in project root, ready for Kaggle upload.

## Notes on Models
- **ARIMA baseline**: strong when each system’s series is short, shows daily seasonality, and stationarity can be induced—often outperforming heavy ML that needs lots of per‑system history.
- **XGBoost/LSTM baselines** are included for fair comparisons and future improvements.
