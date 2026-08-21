# 📈 FINNOVA Stock Predictor

An AI-powered **Indian Stock Market Prediction Web Application** built using **Python, Flask, Machine Learning, and Yahoo Finance**.

The application fetches historical and near real-time stock data for Indian NSE stocks, trains a **Logistic Regression** machine learning model, and predicts whether the stock price is likely to move **Up 📈 or Down 📉**.

---

## 🚀 Features

* 📊 Indian NSE stock prediction
* ⚡ Near real-time stock price and volume
* 📈 Historical stock price data
* 🤖 Machine Learning-based prediction
* 🧠 Logistic Regression model
* 📏 Feature scaling using StandardScaler
* 📉 Interactive stock price chart
* 🌐 Flask-based web interface
* 🎨 Custom financial background
* 📱 Responsive web interface

---

## 🧠 How It Works

The application follows these steps:

```text
User enters NSE Stock Symbol
            ↓
Fetch historical data from Yahoo Finance
            ↓
Prepare and clean the dataset
            ↓
Calculate previous closing price
            ↓
Calculate price movement
            ↓
Create Up/Down target
            ↓
Split data into Training & Testing sets
            ↓
Standardize features
            ↓
Train Logistic Regression model
            ↓
Fetch latest stock price & volume
            ↓
Predict Stock Direction
            ↓
Display Up 📈 / Down 📉
```

---

## 🤖 Machine Learning Model

The project uses **Logistic Regression** for binary classification.

### Input Features

The model uses:

* `Prev_Close` – Previous day's closing price
* `Volume` – Trading volume

### Target

The target is created from the stock price movement:

```text
Price Change > 0  →  Up
Price Change ≤ 0  →  Down
```

The prediction output is:

```text
Up
```

or

```text
Down
```

---

## 📊 Data Source

The application uses **Yahoo Finance** through the `yfinance` Python library.

It retrieves:

* Historical stock prices
* Closing prices
* Trading volume
* Near real-time stock information

### Supported Stocks

The application is designed for **Indian NSE stocks**.

For example:

```text
RELIANCE
TCS
INFY
HDFCBANK
ICICIBANK
SBIN
ITC
```

The application automatically adds `.NS` to the entered symbol.

Example:

```text
RELIANCE
      ↓
RELIANCE.NS
```

---

## 🛠️ Technologies Used

| Technology          | Purpose                    |
| ------------------- | -------------------------- |
| Python              | Backend & ML               |
| Flask               | Web framework              |
| yFinance            | Stock market data          |
| Pandas              | Data processing            |
| Scikit-learn        | Machine Learning           |
| Logistic Regression | Stock direction prediction |
| StandardScaler      | Feature scaling            |
| Chart.js            | Stock visualization        |
| HTML/CSS            | Web interface              |
| JavaScript          | Frontend interaction       |
| Gunicorn            | Production server          |

---

## 📁 Project Structure

```text
stock-predictor/
│
├── app.py
│   ├── Flask application
│   ├── Stock data collection
│   ├── Data preprocessing
│   ├── ML model
│   └── Prediction API
│
├── background.jpg
│   └── Application background
│
├── requirements.txt
│   └── Python dependencies
│
└── README.md
    └── Project documentation
```

---

# ⚙️ Installation

## 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/stock-predictor.git
```

Navigate to the project:

```bash
cd stock-predictor
```

---

## 2. Create a Virtual Environment

### Windows

```bash
python -m venv venv
```

Activate it:

```bash
venv\Scripts\activate
```

### Linux / macOS

```bash
python3 -m venv venv
```

Activate it:

```bash
source venv/bin/activate
```

---

## 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

# ▶️ Run the Application

Start the Flask application:

```bash
python app.py
```

Then open your browser and visit:

```text
http://127.0.0.1:5000
```

---

# 📈 Using the Application

1. Open the FINNOVA Stock Predictor.
2. Enter an Indian NSE stock symbol.
3. Click **Predict**.
4. The application retrieves market data.
5. The ML model processes the historical data.
6. The predicted direction is displayed.
7. Historical stock information is visualized through a chart.

### Example

```text
Stock Symbol:
RELIANCE

Prediction:
📈 Up
```

---

# 🔬 Model Training

Historical data for approximately **3 months** is retrieved from Yahoo Finance.

The dataset is processed using:

```python
df["Prev_Close"] = df["Close"].shift(1)

df["Price_Change"] = df["Close"] - df["Prev_Close"]

df["Target"] = (df["Price_Change"] > 0).astype(int)
```

The data is then divided into training and testing sets:

```python
train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)
```

Features are standardized using:

```python
StandardScaler()
```

Finally, the Logistic Regression model is trained:

```python
LogisticRegression()
```

---

# 🌐 Application Architecture

```text
                 ┌─────────────────────┐
                 │       User          │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │   Flask Web UI      │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │    Flask API        │
                 └──────────┬──────────┘
                            │
                ┌───────────┴───────────┐
                ▼                       ▼
       ┌─────────────────┐     ┌─────────────────┐
       │ Yahoo Finance   │     │ Historical Data │
       │ Real-time Data  │     │   Processing    │
       └────────┬────────┘     └────────┬────────┘
                │                       │
                └───────────┬───────────┘
                            ▼
                 ┌─────────────────────┐
                 │ Logistic Regression │
                 │    ML Model         │
                 └──────────┬──────────┘
                            │
                            ▼
                  ┌──────────────────┐
                  │ Up 📈 / Down 📉 │
                  └──────────────────┘
```

---

# 🔮 Future Improvements

The project can be enhanced with:

* [ ] LSTM-based stock forecasting
* [ ] Random Forest prediction
* [ ] XGBoost prediction
* [ ] Multiple technical indicators
* [ ] RSI analysis
* [ ] MACD analysis
* [ ] Moving averages
* [ ] Trading volume analysis
* [ ] Financial news sentiment analysis
* [ ] Stock comparison
* [ ] Portfolio management
* [ ] Model accuracy dashboard
* [ ] Prediction confidence score
* [ ] Backtesting
* [ ] User authentication
* [ ] Database integration
* [ ] Docker deployment
* [ ] Cloud deployment

---

# ⚠️ Disclaimer

This project is developed for **educational and research purposes**.

Stock market predictions generated by this application are based on historical data and machine learning algorithms. They **do not guarantee future stock performance**.

The application should not be considered professional financial or investment advice.

Always conduct your own research and consult a qualified financial advisor before making investment decisions.

---

# 👨‍💻 Project Information

**Project:** FINNOVA Stock Predictor
**Domain:** Artificial Intelligence & FinTech
**Type:** Machine Learning Web Application
**Language:** Python
**Framework:** Flask
**ML Algorithm:** Logistic Regression
**Data Source:** Yahoo Finance

---

## ⭐ If You Like This Project

If you found this project useful or interesting, consider giving the repository a ⭐ on GitHub.

**FINNOVA — Predict. Analyze. Invest Smarter. 📈🤖**
