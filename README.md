# Flight Price Prediction

This project explores airline ticket price prediction using multiple methodologies, ranging from standard preprocessing to advanced feature engineering and dimensionality reduction. The primary goal was to achieve high predictive accuracy while optimizing for computational efficiency.

##  Repository Structure

The repository is organized into three distinct stages to demonstrate the evolution of the model:

1.  **`01_Exploratory_Data_Analysis.ipynb`**: Investigates data distributions and relationships, identifying key patterns like the multimodal nature of departure times.
    
2.  **`02_Method1_Standard_Pipeline.ipynb`**: Establishes a baseline performance using standard One-Hot Encoding and power and function transformers.
    
3.  **`03_Method2_Optimized_Pipeline_PCA.ipynb`**: Implements advanced techniques including custom binning, and PCA optimization.
    

----------

## Results Comparison

### Method 1: Standard Baseline

Using a basic preprocessing approach, the models achieved the following scores:

-   **Random Forest**: $R^{2}$ 0.7677 | MAE: 0.17
    
-   **KNN**: $R^{2}$ 0.7603 | MAE: 0.19
    
-   **Linear Regression**: $R^{2}$ 0.7225 | MAE: 0.21
    
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/d6ebc77e-aba4-4cf7-a6c2-cf496db9dc87" />

### Method 2: Optimized Pipeline with PCA & Binning

After applying domain-specific binning for `dep_hour` , the model performance remained robust even with significantly reduced dimensions.

> **Key Insight**: While the absolute $R^{2}$ scores showed nominal change between the methods, the **efficiency gain** was substantial.

<img width="1136" height="612" alt="image" src="https://github.com/user-attachments/assets/f3b106e7-c4bf-4b60-9422-b881b633caa1" />

----------

## 🔬 PCA Optimization Discovery

A sensitivity analysis was performed to determine the relationship between the number of Principal Components and model accuracy.

Observation on KNN Performance:

The PCA analysis revealed a significant "plateau" effect for the K-Nearest Neighbors model.

-   **Efficiency Milestone**: KNN achieved nearly identical performance at **25 components** as it did at **50 components**.
    
-   **Conclusion**: We can reduce the feature space by 50% without sacrificing predictive power, leading to faster inference times in a production environment.
    

----------

##  Techniques Applied

-   **Custom Binning**: Grouped `dep_hour` into 4 distinct time-of-day categories to capture non-linear pricing trends.
    
-   **Log Transformation**: Applied to `duration` to stabilize variance and normalize its right-skewed distribution.
    
-   **Mixed Encoding**: Combined **Ordinal Encoding** for `Total_Stops` and **One-Hot Encoding** for nominal features like `Airline`.
    
-   **Dimensionality Reduction**: Utilized PCA to compress a 52-column feature set into a more manageable latent space


##  Conclusion

The **Random Forest** model emerged as the most robust predictor, handling the abstract PCA components more effectively than linear methods. However, the most significant insight was the **KNN PCA plateau**, which demonstrated that high-dimensional flight data can be successfully compressed without sacrificing predictive integrity.


## How to Reproduce

1.  Clone the repository:
    Bash
    ```
    git clone https://github.com/Prasukjain271/flight-price-prediction-pipeline.git
    
    ```
    
2.  Install dependencies
    Bash
    ```
    pip install -r requirements.txt
    
    ```
3.  Run the notebooks in sequence from `01` to `03`.
