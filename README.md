# 🩺 MediPredict — Multi-Disease Prediction System

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python)
![Flask](https://img.shields.io/badge/Flask-3.0.3-black?logo=flask)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.3.2-orange?logo=scikit-learn)
![License](https://img.shields.io/badge/License-MIT-green)

A machine learning web application that predicts the risk of **Heart Disease**, **Diabetes**, and **Liver Disease** from clinical parameters — built with Flask, scikit-learn, and a clean single-page UI.

> ⚠️ **Disclaimer:** This tool is for educational purposes only and is **not a substitute for professional medical advice**.

---

## 📸 Demo

![MediPredict Demo](assets/demo.gif)

---

## ✨ Features

- 🫀 **Heart Disease** prediction using Random Forest (5 clinical features)
- 🩸 **Diabetes** prediction using Gradient Boosting (8 features)
- 🫁 **Liver Disease** prediction using Logistic Regression (10 features)
- 📊 Confidence score displayed with every prediction
- ⚡ On-demand model training via the UI (no CLI required)
- 🌐 Clean, single-page web interface — no JavaScript frameworks needed

---

## 🏗️ Project Structure

```
disease_prediction/
├── app.py              ← Flask backend — routes, model loading, prediction API
├── train_models.py     ← ML training pipeline (synthetic → swap for real data)
├── requirements.txt    ← Pinned dependencies
├── models/             ← Serialized .pkl files (auto-generated, git-ignored)
├── templates/
│   └── index.html      ← Single-page frontend
└── .vscode/
    └── launch.json     ← VS Code debug config (F5 to run)
```

---

## 🔬 ML Models

| Disease   | Algorithm             | Features | Training Data       |
|-----------|-----------------------|----------|---------------------|
| Heart     | Random Forest         | 5        | Synthetic (see note)|
| Diabetes  | Gradient Boosting     | 8        | Synthetic (see note)|
| Liver     | Logistic Regression   | 10       | Synthetic (see note)|

> **Note:** Models are currently trained on synthetic data. See [Upgrading to Real Datasets](#-upgrading-to-real-datasets) to swap in real clinical data.

---

## 🚀 Quick Start

### Prerequisites
- Python 3.10 or higher
- `pip`

### Setup

```bash
# 1. Clone the repository
get clone https://github.com/mithun0207-AM/-MediPredict-Multi-Disease-Prediction-System.git
cd disease-prediction

# 2. Create and activate a virtual environment
python -m venv venv

# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Train the models (first-time only)
python train_models.py

# 5. Start the app
python app.py
```

Then open **http://127.0.0.1:5000** in your browser.

---

## 🐳 Running with Docker _(optional)_

```bash
docker build -t medipredict .
docker run -p 5000:5000 medipredict
```

> A `Dockerfile` is not yet included — contributions welcome!

---

## 🐛 VS Code Debugging

1. Open the project folder in VS Code
2. Press **F5** → select **"Flask: Debug"**
3. Set breakpoints in `app.py` or `train_models.py`

---

## 📡 API Reference

### `POST /predict`

Predict disease risk from input features.

**Request body:**
```json
{
  "disease": "heart",
  "features": [63, 1, 3, 145, 0]
}
```

**Response:**
```json
{
  "prediction": "⚠️ Heart Disease Risk Detected",
  "confidence": "87.3%",
  "is_positive": true
}
```

| Disease    | `disease` value | Number of features |
|------------|-----------------|--------------------|
| Heart      | `"heart"`       | 5                  |
| Diabetes   | `"diabetes"`    | 8                  |
| Liver      | `"liver"`       | 10                 |

### `POST /train`

Re-trains all models on demand.

---

## 📈 Upgrading to Real Datasets

Replace the synthetic data in `train_models.py` with these well-known public datasets:

| Disease   | Dataset                                    | Source  |
|-----------|--------------------------------------------|---------|
| Heart     | [UCI Heart Disease Dataset][heart]         | Kaggle  |
| Diabetes  | [Pima Indians Diabetes Dataset][diabetes]  | Kaggle  |
| Liver     | [Indian Liver Patient Dataset][liver]      | Kaggle  |

[heart]: https://www.kaggle.com/datasets/ronitf/heart-disease-uci
[diabetes]: https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database
[liver]: https://www.kaggle.com/datasets/uciml/indian-liver-patient-records

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

1. Fork the repo
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m "feat: add your feature"`
4. Push and open a Pull Request

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## 👤 Author

**Your Name**
- GitHub: [@mithun0207-AM](https://github.com/mithun0207-AM)
