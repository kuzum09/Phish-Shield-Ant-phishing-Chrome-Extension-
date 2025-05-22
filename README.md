# 🛡️Phish-Shield Anti-Phishing Chrome Extension

PhishShield is a Chrome extension that uses machine learning to detect phishing websites in real time. It analyzes URL-based features and provides users with immediate risk assessments, offering proactive protection against malicious sites. With its lightweight design, smart UI feedback, and high detection accuracy, PhishShield ensures both security and usability for all users—technical or not.

---

## 🚀 Features

- 🔍 **Real-Time URL Analysis** using ML classification
- 🎯 **97.3% Accuracy** with XGBoost on benchmark datasets
- 🟢🔴 **Color-Coded Verdicts**: Instantly identify safe (green) and phishing (red) pages
- 📊 **Probability-Based Scoring** (e.g., "70% legitimate")
- 📋 **Risk Factor Cards** explaining model decisions (e.g., SSL, domain age)
- 🎨 **Modern UI** with dynamic feedback and animation
- ⚡ **Low Latency Inference** with FastAPI backend

---

## 📦 Dataset

- **Phishing URLs**: Sourced from [PhishTank](https://phishtank.org/) and [OpenPhish](https://openphish.com/)
- **Legitimate URLs**: Extracted from [Alexa Top 1 Million](https://www.alexa.com/topsites)
- **Dataset Size**: 10,000 labeled URLs (50% phishing, 50% legitimate)

---

## 🧠 Model Training

- **Language**: Python 3.9
- **Libraries**: `scikit-learn`, `XGBoost`, `Keras`, `Pandas`, `NumPy`, `FastAPI`
- **Best Performing Model**: `XGBoost` (Accuracy: 97.3%)
- **Metrics**: Accuracy, Precision, Recall, F1 Score, ROC-AUC
- **Train/Test Split**: 80% / 20%

---

## 🖥️ Project Architecture

```
Client (Chrome Extension)
│
├── manifest.json
├── popup.html / popup.js / styles.css
│
└── Calls
      ↓
Backend (FastAPI Server)
│
├── phishing_model.pkl (Trained XGBoost)
├── predict.py
└── utils.py
```

---

## 📷 Screenshots

| Extension Installed | Phishing Detected | Legitimate Page |
|---------------------|-------------------|------------------|
| ![Extension Installed](https://github.com/user-attachments/assets/daebf220-6ff9-407c-b330-dc5adbff94df) | ![Phishing Detected](https://github.com/user-attachments/assets/438fedd8-f623-4f70-a9b7-a8d6fff58c98) | ![Legitimate Page](https://github.com/user-attachments/assets/c7db5e14-be6b-4f7e-ba35-65aaea9960cd) |


---

## 🔧 Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/phishshield.git
cd phishshield
```

### 2. Set Up Virtual Environment (Optional but Recommended)

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Train or Load Pre-trained Model

> Skip this step if `phishing_model.pkl` already exists.

```bash
python train_model.py
```

### 5. Run the Backend (FastAPI)

```bash
uvicorn app:app --reload
```

### 6. Load Extension in Chrome

1. Open `chrome://extensions/`
2. Enable **Developer mode**
3. Click **Load unpacked** and select the `chrome_extension/` folder

---

## 💡 How It Works

1. User enters or navigates to a URL
2. URL is sent to FastAPI server
3. Server extracts features and runs it through ML model
4. Model returns:
   - Prediction (Phishing or Legitimate)
   - Confidence Score
   - Risk Factor Analysis
5. Result displayed to the user in real time

---

## 🛠️ Tech Stack

| Layer        | Tools Used                             |
|--------------|----------------------------------------|
| Language     | Python, JavaScript                     |
| ML Backend   | XGBoost, Scikit-learn, FastAPI         |
| Frontend     | HTML/CSS/JS for Chrome Extension       |
| Deployment   | Localhost (can be Dockerized or cloud) |

---

## 🔮 Future Work

- 🧠 Integration of Deep Learning (RNN/Transformer-based) models
- 📈 Live Threat Feed Sync (e.g., Google Safe Browsing)
- 📱 Mobile and Firefox/Edge support
- 🧾 HTML & Visual Phishing Page Detection
- 🌐 Centralized Admin Dashboard (Enterprise use)
- 🔁 User feedback loop for model retraining

---


## ⭐ Acknowledgements

- [PhishTank](https://phishtank.org/)
- [OpenPhish](https://openphish.com/)
- [Alexa Top Sites](https://www.alexa.com/topsites)
- FastAPI, Scikit-learn, XGBoost
