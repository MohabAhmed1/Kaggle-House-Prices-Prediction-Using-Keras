# House Prices Prediction (Keras)

Predicting house prices using a neural network built with **Keras / TensorFlow**. This project includes data preprocessing, log-transformed target, feature standardization, and a complete pipeline for training, validation, and generating Kaggle submissions.

---

## 📌 Objective
Predict the `SalePrice` of residential homes using the Kaggle dataset: [House Prices – Advanced Regression Techniques](https://www.kaggle.com/c/house-prices-advanced-regression-techniques).

---

## 🧠 Model Details
- **Framework:** Keras (TensorFlow backend)
- **Architecture:** 
  - Input layer → Dense(128, ReLU) → Dropout(0.4)
  - Dense(64, ReLU) → Dropout(0.4)
  - Output layer → 1 neuron (predicts log(SalePrice))
- **Loss Function:** Mean Squared Error (MSE)
- **Metric:** Mean Absolute Error (MAE)
- **Target:** Log-transformed SalePrice (`np.log1p`)
- **Callbacks used:**  
  - **EarlyStopping**: stops training if validation loss doesn’t improve (patience=20)  
  - **ReduceLROnPlateau**: reduces learning rate if validation loss plateaus (factor=0.5, patience=10)

---

## 🗂 Data Preprocessing
- Keep only **numeric features**.  
- Drop `Id` column.  
- Fill missing numeric values with **training mean**.  
- **Standardize features** using training mean & std (mean=0, std=1).  
- Split data into **training** and **validation** sets before scaling.  
- Apply the **same preprocessing** to the test set before prediction.

---

## 🚀 Training
- Model trained for up to **500 epochs** with **batch size 32**.  
- **Early stopping** ensures no overfitting, and **learning rate reduction** helps convergence.  
- Training and validation MAE monitored to track performance.

---

## 📊 Results
- **Validation MAE (log scale):** ~0.11 (~11% relative error)  
- **Kaggle RMSLE (public leaderboard):** **0.1690** ✅  
- **Submission:** `submission.csv` ready for upload to Kaggle.

---

## 🚀 Usage
1. Clone the repository:
```bash
git clone https://github.com/your-username/house-prices-keras.git
cd house-prices-keras
