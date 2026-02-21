# MLG382A2 — Airline Delay / Prediction Project

Authors
- Tyler Geuens — 600153
- Francois Myburg — 600576
- Marco Reiners — 578056
- Luan Mahoney — 600617

## Project overview

This repository contains the code, data and a trained model used for the MLG382 assignment. The goal of the project is to explore and model airline-related data (stored in `Invistico_Airline.csv`), evaluate model performance, and provide a small application and a notebook for inspecting or reproducing results.

This README explains the repository layout, how to run the code on a Windows system (PowerShell), how to inspect or retrain the model, and where to find each artifact.

## Repository structure

- `App.py` — Main script (entry point). Depending on the project, this may load the trained model (`nn_model.keras`) and run inference or a small demo. Inspect the file to confirm behavior.
- `Invistico_Airline.csv` — Dataset used for experiments. Contains the raw data used to train or evaluate the model. Open the CSV to see the exact column names and types.
- `nn_model.keras` — Trained neural network model saved in Keras format. Can be loaded with TensorFlow / Keras for inference or further training.
- `requirements.txt` — Python dependencies required to run the project.
- `TestNB.ipynb` — Jupyter Notebook with exploratory analysis, modeling experiments, and example training/evaluation steps.
- `Readme.md` — This file.

## Requirements

This project uses Python. Install dependencies listed in `requirements.txt`. Typical packages include (but may not be limited to):

- tensorflow (for model loading and training)
- pandas, numpy (data handling)
- scikit-learn (preprocessing / metrics)
- jupyter (to run the notebook)

Install dependencies with PowerShell (from the repository root):

```powershell
python -m venv .venv; .\.venv\Scripts\Activate.ps1; python -m pip install --upgrade pip; pip install -r requirements.txt
```

If you prefer not to create a virtual environment, run:

```powershell
python -m pip install --upgrade pip; pip install -r requirements.txt
```

## How to run

1. Activate your virtual environment (if created):

```powershell
.\.venv\Scripts\Activate.ps1
```

2. To run the main application (behavior depends on `App.py`):

```powershell
python App.py
```

3. To inspect the data and reproduce experiments, open `TestNB.ipynb` in Jupyter (or VS Code's notebook UI):

```powershell
jupyter notebook TestNB.ipynb
```

4. To load the provided model programmatically (example):

```python
from tensorflow import keras
model = keras.models.load_model('nn_model.keras')
# then run model.predict on prepared inputs
```

Note: The exact input preprocessing required by the model is documented in the notebook and (where applicable) in `App.py`. Check those files for feature order, scalers, and categorical encodings.

## Reproducing results / Training

- The repository includes `nn_model.keras` as a saved artifact. Use `TestNB.ipynb` as the canonical reproduction script: it contains data loading, preprocessing, training, evaluation, and visualization steps.
- If you want to retrain from scratch, open the notebook and run the training cells. Alternatively, create a new Python script that follows the same preprocessing and model architecture.

Suggested high-level training steps:
1. Load `Invistico_Airline.csv` with `pandas.read_csv`.
2. Inspect and clean missing values.
3. Encode categorical variables and scale numerical features.
4. Split into train/validation/test sets.
5. Define the Keras model, compile and fit.
6. Save the trained model with `model.save('nn_model.keras')`.

## Notes and assumptions

- The exact feature names and target variable are stored in `Invistico_Airline.csv` and referenced in `TestNB.ipynb` and `App.py`. If you change column names, update preprocessing accordingly.
- The included model file (`nn_model.keras`) may have been trained with a specific version of TensorFlow. If you encounter errors when loading, try matching the TensorFlow version from `requirements.txt`.

## Quick troubleshooting

- If `python App.py` fails with a missing dependency error, ensure you installed requirements in the activated environment.
- If loading `nn_model.keras` raises compatibility errors, check TensorFlow versions and consider retraining via the notebook.

## License & contact

This project is created for the MLG382 course. For questions about the code or dataset, contact the authors listed above.

---

If you'd like, I can also:
- Add a separate `README-developers.md` with development notes and a CONTRIBUTING section.
- Add a small example script `examples/predict_example.py` showing how to call the model on a single CSV row.

If you want any of those, tell me which and I'll add them.
