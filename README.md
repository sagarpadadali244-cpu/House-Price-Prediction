# 🏠 Bengaluru House Price Prediction

A machine learning web application that predicts house prices in Bengaluru based on location, total area, number of bedrooms (BHK), bathrooms, and area type. The project covers data cleaning, feature engineering, outlier removal, model training, and deployment through a Flask web app.

## ✨ Features

- Cleans and preprocesses the raw Bengaluru housing dataset
- Engineers features such as `bhk` and `price_per_sqft`
- Removes unrealistic listings and per-location price outliers
- Groups rare locations (10 or fewer listings) into an `other` category
- Trains a Linear Regression model and reports R², MAE, and RMSE
- Includes scripts for model comparison, hyperparameter tuning, and feature importance
- Flask web interface for getting live price predictions

## 🛠️ Tech Stack

- **Language:** Python
- **Data and ML:** Pandas, NumPy, Scikit-learn, Joblib
- **Visualization:** Matplotlib
- **Web:** Flask, Jinja2, HTML/CSS (Gunicorn for production)

## 📁 Project Structure

```
house-price-prediction/
├── dataset/                  # Raw and cleaned housing data (bengaluru_house_prices.csv)
├── model/                    # Saved model (house_price_model.pkl) and columns.json
├── screenshots/              # App screenshots
├── static/                   # CSS / JS / static assets
├── templates/                # HTML templates for the Flask app
├── app.py                    # Flask web application
├── train_model.py            # Data cleaning, feature engineering, training
├── compare_models.py         # Compare different regression models
├── hyperparameter_tuning.py  # Tune model hyperparameters
├── feature_importance.py     # Analyze feature importance
├── predict.py                # Run predictions from the saved model
├── requirements.txt          # Python dependencies
├── LICENSE
└── README.md
```

## 🔄 How It Works

1. **Load data:** reads `dataset/bengaluru_house_prices.csv`
2. **Clean:** drops the `society` column and rows with missing values
3. **Feature engineering:** extracts `bhk` from the `size` column, converts `total_sqft` ranges (e.g. `1133-1384`) to their average, and computes `price_per_sqft`
4. **Filter impossible houses:** removes listings with less than 300 sqft per bedroom
5. **Handle locations:** strips whitespace and merges rare locations into `other`
6. **Remove outliers:** drops listings outside one standard deviation of the mean price per sqft within each location
7. **Encode:** one-hot encodes `location` and `area_type`
8. **Train:** 80/20 train-test split (`random_state=42`) with Linear Regression
9. **Save:** stores the model as `model/house_price_model.pkl` and the feature list as `model/columns.json`

## 📊 Results

| Metric | Score |
|--------|-------|
| R² | [add your value] |
| MAE | [add your value] |
| RMSE | [add your value] |

Run `python train_model.py` to see the metrics for your setup.

## 🚀 Getting Started

### Prerequisites

- Python 3.9 or higher
- pip

### Installation

```bash
# Clone the repository
git clone https://github.com/Jeevan-can-code/house-price-prediction.git
cd house-price-prediction

# (Optional) create a virtual environment
python -m venv venv
source venv/bin/activate      # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Train the model

```bash
python train_model.py
```

This cleans the data, trains the model, and saves the outputs to the `model/` folder.

### Run the web app

```bash
python app.py
```

Then open the local URL shown in your terminal.

### Optional scripts

```bash
python compare_models.py          # compare regression models
python hyperparameter_tuning.py   # tune hyperparameters
python feature_importance.py      # view feature importance
python predict.py                 # predict from the command line
```

## 📸 Screenshots

Screenshots of the app are available in the [`screenshots`](screenshots/) folder.

## 🔮 Future Improvements

- Try ensemble models such as Random Forest or Gradient Boosting
- Add more features such as amenities and proximity to metro or tech parks
- Deploy online (Render, Railway, or similar)
- Add input validation and price range estimates

## 🤝 Contributing

Contributions are welcome. Fork the repo, create a branch, and open a pull request.

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## 👤 Author

**Sagar S P**
GitHub: [@sagarpadadali244-cpu](https://github.com/sagarpadadali244-cpu)
