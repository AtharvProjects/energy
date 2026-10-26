# Energy Consumption Prediction — ISE Activity

## 1. Objective

The objective of this activity is to explore energy-consumption data and document a machine-learning regression task that estimates energy consumption (in kWh) from time, weather, occupancy, and appliance-usage features.

## 2. Software, Tools, and Technologies

- **GitHub** — source and project-file hosting
- **CSV** — tabular dataset format
- **JSON** — model metadata and evaluation metrics
- **Python (recommended for data inspection)** — Python 3.x with pandas and scikit-learn if you are extending the project

> The repository currently contains the dataset and model metadata. A training/inference script and dependency file are not included yet, so this README does not claim that a complete prediction application can already be run.

## 3. Repository Contents

| File | Description |
|---|---|
| `energy_data.csv` | Dataset containing input features and the target `energy_kwh` |
| `model_info.json` | Recorded model feature list, evaluation metrics, and feature-importance values |
| `README.md` | Activity documentation and instructions |

## 4. Dataset Description

The dataset contains the following columns:

| Column | Description |
|---|---|
| `hour` | Hour of the day (0–23) |
| `day_of_week` | Day index (0–6; confirm the weekday mapping used by the data generator) |
| `temperature_c` | Temperature in degrees Celsius |
| `humidity_pct` | Relative humidity percentage |
| `occupants` | Number of occupants represented in the record |
| `appliances_on` | Appliance-usage count/value represented in the record |
| `is_holiday` | Holiday indicator (0 or 1) |
| `energy_kwh` | Target energy consumption in kWh |

## 5. Execution / Inspection Steps

### Step 1 — Clone the repository

```bash
git clone https://github.com/AtharvProjects/energy.git
cd energy
```

### Step 2 — Check the project files

```bash
ls
```

Confirm that `energy_data.csv` and `model_info.json` are present.

### Step 3 — Set up Python for dataset inspection (optional)

Create and activate a virtual environment, then install pandas:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install pandas
```

On Windows, activate the environment with:

```powershell
.venv\Scripts\Activate.ps1
```

### Step 4 — Inspect the dataset

Run this one-line command from the repository directory:

```bash
python -c "import pandas as pd; df=pd.read_csv('energy_data.csv'); print(df.head()); print('Shape:', df.shape); print(df.isnull().sum())"
```

### Step 5 — Read the model metadata

Open `model_info.json` in a text editor or run:

```bash
python -m json.tool model_info.json
```

**Note:** These steps inspect the data and metadata. They do not run a prediction model. To make end-to-end predictions, add the actual model/training code and its dependencies, and document the exact command here.

## 6. Recorded Results

The current `model_info.json` records these evaluation metrics:

| Metric | Recorded value | Interpretation |
|---|---:|---|
| R² | 0.9506 | Reported coefficient of determination |
| MAE | 0.2277 | Reported mean absolute error |
| RMSE | 0.2856 | Reported root mean squared error |

The metadata lists `appliances_on` as the largest feature-importance value (approximately 0.6331), followed by `temperature_c` (approximately 0.2074) and `occupants` (approximately 0.0963).

These are values recorded in the repository metadata; the training procedure, evaluation split, model type, and metric units should be documented alongside the training code before the results are treated as independently reproducible.

## 7. Sample Input and Output

Example input feature row (illustrative):

```text
hour=18, day_of_week=5, temperature_c=31.4, humidity_pct=68.4,
occupants=2, appliances_on=14, is_holiday=0
```

The corresponding dataset row records `energy_kwh=5.368`. This is an example from the CSV, **not a newly generated model prediction**.

For evaluation screenshots, capture:
1. The repository file list on GitHub.
2. The output of the dataset inspection command.
3. The formatted `model_info.json` metrics.
4. Once prediction code is added, a genuine run showing input features and predicted energy consumption.

## 8. Results and Conclusion

The repository provides a structured energy-consumption dataset and metadata describing a regression model's reported performance and feature importance. The recorded results suggest that appliance usage and temperature are influential features in the stored model metadata. The current repository is suitable for inspecting the data and metadata; a reproducible, executable prediction workflow still requires the training/inference source code, dependency list, and documented validation procedure.

## 9. Author

**Atharv Mane**  
GitHub: [AtharvProjects](https://github.com/AtharvProjects)

---

*ISE activity repository. Update this documentation if the dataset, model, execution commands, or results change.*
