# House-Price-Prediction

## 📌 Project Overview

The **House Price Prediction** project is a machine learning application developed using Python and Flask. It predicts house prices based on different property features such as bedrooms, bathrooms, living area, lot area, floors, condition, location, and year of construction.

This project uses the **Multiple Linear Regression** algorithm to train a prediction model. The trained model is saved using Pickle and integrated with a Flask web application to provide house price predictions through a user-friendly interface.

## 🎯 Objectives

- To predict house prices using machine learning.
- To analyze different features that influence house prices.
- To preprocess and prepare the dataset for model training.
- To implement Multiple Linear Regression.
- To evaluate the trained model using prediction error metrics.
- To develop a web application using Flask.
- To provide an interactive interface for users to predict house prices.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | Programming language |
| Pandas | Data loading and manipulation |
| NumPy | Numerical operations |
| Matplotlib | Data visualization |
| Scikit-learn | Machine learning |
| Linear Regression | Prediction algorithm |
| Flask | Web application development |
| HTML | Web page structure |
| CSS | Web page styling |
| Pickle | Saving and loading the trained model |
| Jupyter Notebook | Model development and experimentation |

## 📂 Project Structure

```text
House-Price-Prediction/
│
├── main.py
├── app.py
├── data.csv
├── model.pkl
│
├── templates/
│   └── index.html
│
├── static/
│   └── pic1.png
│
└── README.md
```

## 📄 File Description

- **main.py** – Performs data preprocessing, model training, testing, evaluation, and saves the trained model.
- **app.py** – Flask application that loads the trained model and handles user predictions.
- **data.csv** – Dataset containing house details and their corresponding prices.
- **model.pkl** – Saved machine learning model.
- **templates/index.html** – Frontend interface for entering house details and displaying predicted prices.
- **static/pic1.png** – Profile image displayed on the web page.
- **README.md** – Project documentation.

## 📊 Dataset Description

The project uses a house price dataset containing approximately **4,600 records and 18 columns**.

### Dataset Features

The dataset contains the following attributes:

| Feature | Description |
|---|---|
| date | Date of house sale |
| price | House selling price (Target Variable) |
| bedrooms | Number of bedrooms |
| bathrooms | Number of bathrooms |
| sqft_living | Living area in square feet |
| sqft_lot | Lot area in square feet |
| floors | Number of floors |
| waterfront | Indicates waterfront availability |
| view | View rating |
| condition | Condition of the house |
| sqft_above | Area above ground |
| sqft_basement | Basement area |
| yr_built | Year of construction |
| yr_renovated | Year of renovation |
| street | Street information |
| city | City where the house is located |
| statezip | State ZIP code |
| country | Country name |

## ⚙️ Project Implementation

### 1. Importing Required Libraries

The following Python libraries are imported:

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import sklearn
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
import sys
import pickle
```

### 2. Loading the Dataset

The dataset is loaded using Pandas.

```python
df = pd.read_csv("data.csv")
```

### 3. Data Preprocessing

The unnecessary columns `date` and `street` are removed from the dataset.

```python
df = df.drop(['date', 'street'], axis=1)
```

Categorical columns such as `city`, `statezip`, and `country` are converted into numerical values so that they can be used by the machine learning model.

### 4. Feature Selection

The independent variables are separated from the dependent variable.

- **Independent variables (X):** House features used for prediction.
- **Dependent variable (y):** House price.

```python
X = df.iloc[:, 1:]
y = df.iloc[:, 0]
```

### 5. Splitting the Dataset

The dataset is divided into training and testing sets.

```python
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)
```

- 80% of the data is used for training.
- 20% of the data is used for testing.

### 6. Model Training

The Multiple Linear Regression algorithm is used to train the model.

```python
self.reg = LinearRegression()
self.reg.fit(self.X_train, self.y_train)
```

### 7. Model Testing

The trained model predicts house prices using the testing dataset.

```python
predictions = self.reg.predict(self.X_test)
```

### 8. Model Evaluation

The project calculates a custom accuracy-like score and an RMSE-style prediction error to evaluate the model's performance.

### 9. Saving the Model

The trained model is saved using the Pickle library.

```python
pickle.dump(self.reg, open("model.pkl", "wb"))
```

## 🌐 Flask Web Application

The trained machine learning model is integrated with Flask to create a web-based prediction system.

### Home Page

The home page displays the project title, profile information, and input fields for entering house details.

### Prediction Page

Users enter the required house features and submit the form. Flask collects the input values and sends them to the trained model.

```python
@app.route('/predict', methods=['GET', 'POST'])
def predict():
    a = [float(i) for i in request.form.values()]
    prediction = p.predict([a])
    return render_template(
        'index.html',
        prediction_text=float(prediction)
    )
```

The predicted house price is displayed on the web page.

## 🔄 Project Workflow

```text
        Dataset (data.csv)
                |
                v
        Data Preprocessing
                |
                v
         Feature Selection
                |
                v
        Train-Test Splitting
                |
                v
       Linear Regression Model
                |
                v
          Model Training
                |
                v
          Model Testing
                |
                v
         Model Evaluation
                |
                v
        Save Model (model.pkl)
                |
                v
        Flask Web Application
                |
                v
         User Input Through HTML
                |
                v
         House Price Prediction
                |
                v
          Display Result
```

## 🚀 How to Run the Project

### Step 1: Clone the Repository

```bash
git clone https://github.com/your-username/House-Price-Prediction.git
```

### Step 2: Open the Project Folder

```bash
cd House-Price-Prediction
```

### Step 3: Install Required Libraries

```bash
pip install numpy pandas matplotlib scikit-learn flask
```

### Step 4: Train the Machine Learning Model

```bash
python main.py
```

This executes the training process and generates `model.pkl`.

### Step 5: Run the Flask Application

```bash
python app.py
```

### Step 6: Open the Application

Open your browser and visit:

```text
http://127.0.0.1:5000/
```

Enter the house details and click the prediction button to view the estimated house price.

## ✨ Key Features

- Machine learning-based house price prediction.
- Multiple Linear Regression algorithm.
- Data preprocessing and categorical encoding.
- Model training and testing.
- Model saving using Pickle.
- Flask-based web application.
- Interactive HTML and CSS user interface.
- Real-time prediction based on user input.

## 🔮 Future Enhancements

- Improve prediction accuracy using advanced regression algorithms.
- Add more housing features to improve predictions.
- Implement data visualization dashboards.
- Improve the user interface and responsiveness.
- Deploy the application on a cloud platform.
- Save and reuse preprocessing mappings for consistent predictions.

## 📚 Learning Outcomes

Through this project, I gained practical experience in:

- Python programming and Object-Oriented Programming.
- Data preprocessing using Pandas and NumPy.
- Machine learning model development.
- Multiple Linear Regression.
- Model evaluation.
- Model serialization using Pickle.
- Flask web application development.
- HTML and CSS frontend development.
- Integrating machine learning models with web applications.

## 🌐 Live Project Deployment

The House Price Prediction application is deployed and accessible online using Render.

Live Application:
👉 https://house-price-prediction-uowh.onrender.com

Users can open the live application, enter house details, and get predicted house prices directly through the web interface without installing the project locally.

## 👩‍💻 Author

**Venkata Siva Bhargavi**

B.Tech – Computer Science and Engineering

**Project:** House Price Prediction Using Multiple Linear Regression

## 📝 Conclusion

The House Price Prediction project demonstrates how machine learning can be used to estimate house prices based on various property characteristics. By combining Python, Multiple Linear Regression, and Flask, this project provides a simple and interactive web application for predicting house prices.

This project helped me understand the complete machine learning workflow, from data preprocessing and model training to deployment through a web application.
