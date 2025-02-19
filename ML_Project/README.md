# FastAPI Machine Learning Model Training and Prediction

This FastAPI application allows users to upload a dataset, train multiple machine learning models, select the best one, and use it for predictions.

## Features

- Upload a CSV dataset.
- Train multiple models (Logistic Regression, KNN, Naive Bayes, SVM, Decision Tree, Random Forest, Gradient Boosting).
- Option to enable or disable hyperparameter tuning.
- Select the best model based on accuracy and predefined ranking.
- Predict outcomes using the trained model.
- Simple web interface using Jinja2 templates.

## Requirements

Install the required dependencies:

```bash
pip install fastapi uvicorn pandas numpy scikit-learn joblib jinja2 python-multipart
```

## Running the Application

Start the FastAPI server:

```bash
uvicorn new:app --reload
```


## API Endpoints

### 1. Upload Dataset and Train Model
- **Endpoint:** `/train`
- **Method:** `POST`
- **Parameters:**
  - `file` (CSV file)
  - `target_column` (String)
  - `hyperparameter_tuning` (String: `"yes"` or `"no"`)

### 2. Make Predictions
- **Endpoint:** `/predict`
- **Method:** `POST`
- **Parameters:** Form data with feature values.

### 3. UI Pages
- `/` → Upload page
- `/predict` → Prediction form

## Folder Structure

```
/project-folder
│── new.py  # FastAPI application script
│── templates/
│   ├── upload.html
│   ├── results.html
│   ├── predict.html
│   ├── error.html
│   ├── predict_results.html
│── static/
│── data/  # Stores uploaded files (temporary)
│── README.md  # Documentation
│── requirements.txt  # Dependencies
```

## Notes

- The best model is automatically selected and stored as `best_model.pkl`.
- If hyperparameter tuning is enabled, GridSearchCV is used.
- Missing values in numerical columns are imputed using the median, and categorical columns use the mode.


---
**Author:** Mann Mavani
