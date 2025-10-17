# BERN02 Semester Project
This is the repository for my semester project in the BERN02 course at Lund University, LTH.

##  Introduction
This project aims to predict whether a seismic event is classified as "strong" based on seismic and weather data. A strong earthquake is defined as having a magnitude greater than 4.4. The objective is to train and evaluate various classification models to identify the key factors that contribute to high-magnitude seismic events.

##  Data Sources
The project utilizes two distinct datasets. For detailed metadata on each dataset, please refer to the files linked below:
* **[Seismic Events Data](./data/events_metadata.md)**: Contains detailed information about each seismic event.
* **[Weather Data](./data/weather_metadata.md)**: Provides weather information corresponding to the event locations and times.

  
##  Methodology
The project follows a structured workflow encompassing data preprocessing, feature engineering, and modeling.

#### 1. Data Preprocessing and Cleaning
* **Data Type Conversion**: Timestamps were converted to the `datetime` format.
* **Data Cleaning**: Numerical columns like `depth` were cleaned of text artifacts.
* **Categorical Feature Encoding**: Features such as `net`, `type`, `horizontalError`, and `is_country` were encoded into a numerical format using `LabelEncoder` and `map` to make them suitable for modeling.
* **Handling Missing Values**: Missing values in numerical columns (`dmin`, `magError`) were imputed using the mean of the respective column.
#### 2. Feature Engineering
* **Target Variable**: The dependent variable, `is_high_magnitude`, was created. It is set to `True` (1) if the magnitude (`mag`) is greater than 4.4, and `False` (0) otherwise.
* **Weather Data Aggregation**: The weather data was grouped by location (`lat`, `lng`) and date. Aggregated daily weather metrics (e.g., mean temperature, total precipitation) were calculated to create a daily weather profile for each location.
* **Data Merging**: The cleaned seismic data was merged with the aggregated weather data to create a final, unified dataset for training.
#### 3. Modeling
Two classification models were trained and evaluated:
1.  **Logistic Regression**: A linear model chosen for its interpretability and ability to highlight feature importance. The model's robustness was assessed using k-fold cross-validation.
2.  **Random Forest**: An ensemble model known for its high predictive accuracy, also used for feature importance evaluation.
The data was split into a training set and a test set (80/20 split) with stratification based on the target variable to maintain the original class distribution.

##  Results
#### Model Performance (Logistic Regression)
The Logistic Regression model demonstrated robust performance, validated through cross-validation:
* **CV Accuracy**: ~87%
* **CV Precision**: ~80%
* **CV Recall**: ~70%
On the hold-out test set, the final model achieved an **accuracy of approximately 89%**.

#### Key Features
Based on the coefficients of the Logistic Regression model, the top five most influential features for predicting a high-magnitude earthquake were:
1.  `net` (Data Contributor)
2.  `is_country` (Event on Land/Sea)
3.  `type` (Type of Event)
4.  `horizontalError` (Positional Uncertainty)
5.  `depthError` (Depth Uncertainty)
   
##  How to Use
To run this project, clone the repository and ensure all necessary dependencies are installed.
1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/lauxenz/BERN02-Semesterproject.git](https://github.com/YOUR_USERNAME/BERN02-Semesterproject.git)
    ```
2.  **Install Dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
3.  **Run the Jupyter Notebook:**
    Open and execute the cells in the `workflow.ipynb` notebook.
##  Dependencies
* `numpy`
* `pandas`
* `scikit-learn`
* `matplotlib`
* `seaborn`
