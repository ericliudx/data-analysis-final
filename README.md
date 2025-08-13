# College Basketball Postseason Prediction

## Overview
This project predicts how far a college basketball team will advance in the postseason based on their regular-season statistics.  
We use a dataset from Kaggle containing team performance stats from past NCAA seasons, and we train several machine learning models to make predictions.

The goal:  
> Given a team's season stats, guess whether they will make the postseason — and if so, how far they’ll go.

---

## Dataset
We use the **College Basketball Dataset** from Kaggle, which contains:
- Team statistics (wins, losses, offensive/defensive ratings, etc.)
- A label for postseason result (e.g., "R68", "R32", "Champions")
- Some missing or non-numeric values that we clean up.

The dataset is downloaded using `kagglehub` in the notebook.

---

## How It Works

### 1. Data Preprocessing
1. **Load the dataset** into Pandas.
2. **Convert postseason results** into numbers (e.g., "R68" → 1, "Champions" → 8, `NaN` → 0 for no postseason).
3. **Scale the numeric data** so all features are in the same range (important for neural networks).
4. **Split into training and testing sets** so we can evaluate our models.

---

### 2. Models We Tried

We experimented with multiple approaches:

#### **A. Neural Network Classifier**
- Input: All season stats (except the postseason label).
- Output: Probability of each postseason round.
- Training: Used TensorFlow/Keras with one-hot encoded labels.

#### **B. Logistic Regression**
- A simpler, classic model to predict postseason participation (yes/no).

#### **C. Hierarchical Classification**
- Step 1: Predict if a team will make the postseason at all (binary classification).
- Step 2: If yes, predict how far they will go (multi-class classification).

---

### 3. Evaluation
- We check **accuracy** for each model on the test set.
- For the hierarchical classifier, we measure both:
  - How well it predicts postseason participation.
  - How well it predicts the correct round for qualifying teams.

---

## Example
If the model sees:
```
Wins: 28
Losses: 4
Offensive Rating: High
Defensive Rating: Low
...
```
It might predict:
```
Postseason: Yes
Predicted Round: Sweet 16
```

---

## Installation
Make sure you have Python 3.9+ and install dependencies:
```bash
pip install pandas numpy scikit-learn tensorflow kagglehub
```

---

## Running the Project
1. Download this repo and open `Final_Project.ipynb` in Jupyter Notebook or VS Code.
2. Run all cells to:
   - Download the dataset
   - Train the models
   - See predictions and evaluation metrics

---

## Future Improvements
- Tune neural network architecture for higher accuracy.
- Add cross-validation for better generalization.
- Visualize feature importance to understand which stats matter most.

---

## Acknowledgments
Dataset from [Kaggle College Basketball Dataset](https://www.kaggle.com/).
