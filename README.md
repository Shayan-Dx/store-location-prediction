# 🏬 Store Location Suitability Prediction

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.3%2B-orange)

## 📋 Overview

This project predicts how **suitable a location is for opening a new store** using machine learning.  
Two complementary models are implemented:

- **Logistic Regression** – classifies a location as **good** or **bad** (binary decision).
- **Linear Regression** – gives a **score from 0 to 100** reflecting the overall suitability.

Both models are trained on AI generated dataset so none of them are based on real-world data.

## 📊 Dataset

The dataset (`dataset/store_location_dataset.csv`) contains **800 samples** with the following features:

| Feature               | Description                                                    |
|-----------------------|----------------------------------------------------------------|
| `dist_metro`          | Walking minutes to the nearest metro station                   |
| `num_residential`     | Number of large residential complexes within 1 km              |
| `avg_income`          | Average household income in the area (million Toman)           |
| `traffic`             | Daily traffic level (`low`, `medium`, `high`)                  |
| `rent_per_sqm`        | Monthly rent per square meter (thousand Toman)                 |
| `has_parking`         | Public parking available (`yes` / `no`)                        |
| `competition_count`   | Number of similar stores within 1 km                           |

The target variables are:
- `score` (0–100) – for the regression model
- `suitable` (`good`/`bad`) – derived from `score >= 50`, used by the classification model

> 📌 The data was generated with realistic correlations (e.g., higher income areas have higher rent, areas near metro stations have more traffic and competition, etc.) and includes Gaussian noise to simulate real uncertainty.

## 📁 Project Structure

```
store-location-prediction/
├── dataset/
│   └── store_location_dataset.csv
├── notebooks/
│   ├── logistic_regression.ipynb
│   └── linear_regression.ipynb
├── requirements.txt
├── README.md
└── .gitignore
```

## 🚀 Setup Instructions

Follow these steps to run the project on any machine (Windows, macOS, or Linux).

### 1. Clone the repository
Open a terminal and clone the repo:
```bash
git clone https://github.com/Shayan-Dx/store-location-prediction.git
cd store-location-prediction
```

### 2. Create a virtual environment (optional but recommended)
```bash
python -m venv venv
```
Activate it:
- **Windows**: `venv\Scripts\activate`
- **macOS/Linux**: `source venv/bin/activate`

### 3. Install dependencies
```bash
pip install -r requirements.txt
```
This installs pandas, numpy, matplotlib, scikit-learn, and jupyter.

### 4. Launch Jupyter Notebook
```bash
jupyter notebook notebooks/
```
Your browser will open with the notebook list.  
Alternatively, you can open a specific notebook directly:
```bash
jupyter notebook notebooks/logistic_regression.ipynb
```

### 5. Run the notebooks
Inside each notebook, select **Kernel → Restart & Run All** to execute all cells and see the output, including model evaluation metrics and visualizations.

> 💡 The notebooks are self‑contained and will load the dataset from `../dataset/store_location_dataset.csv` automatically.

## 🧠 How It Works

- Both models use **StandardScaler** for numerical features and **OneHotEncoder** (with `drop='first'`) for categorical features, packed into a `ColumnTransformer` pipeline.
- The **logistic regression** classifier is trained on the binary target `suitable`.
- The **linear regression** model predicts the continuous `score`; its output is then optionally thresholded at 50 to derive a good/bad decision – making the two approaches directly comparable.

Performance is assessed with:
- Accuracy, Confusion Matrix, Precision/Recall/F1, ROC AUC (classification)
- MAE, MSE, RMSE, R², Residual Plots (regression)
- 5‑fold cross‑validation for stability

## 📈 Key Results

| Model                  | Main Metric     | Value   |
|------------------------|-----------------|---------|
| Logistic Regression    | ROC AUC         | ~0.95   |
| Logistic Regression    | Accuracy        | ~89%    |
| Linear Regression      | R²              | ~0.85   |
| Linear Regression      | MAE (score)     | ~6.3    |
| Linear Reg. → Classify | Accuracy        | ~92%    |

The models not only achieve high accuracy but also show **interpretable coefficients** that align with business intuition (e.g., proximity to metro increases suitability, low traffic decreases it, high competition reduces the score).

## 📦 Dependencies

All required packages are listed in `requirements.txt`:
- pandas
- numpy
- matplotlib
- scikit-learn
- jupyter

Install them with `pip install -r requirements.txt`.

## 📝 License

This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details (you can add a `LICENSE` file if you wish).

## 🤝 Contributing

This project was developed as a demonstration of machine learning fundamentals. Feedback, suggestions, and pull requests are welcome!

---

**Built with ❤️ and Python, powered by scikit‑learn.**