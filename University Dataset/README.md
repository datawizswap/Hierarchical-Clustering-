# University Clustering
#### Overview
This project performs Hierarchical Clustering on a university dataset to group universities based on various features like SAT scores, acceptance rates, and student-faculty ratios. It includes data preprocessing, handling missing values, detecting and treating outliers, and applying clustering techniques to discover patterns in the data.

The clustering process helps in identifying university groups that share similar characteristics, which can be useful for various educational analyses.

##  Features 
#### Data Preprocessing: Handling missing values using mean, median, and random imputers.
#### Outlier Detection: Using Winsorization to treat outliers in key variables such as SAT scores and acceptance rates.
#### Hierarchical Clustering: Building dendrograms and using Ward's method for clustering.
#### Correlation Analysis: Visualizing relationships between variables through correlation matrices.
#### Silhouette Score: Evaluating the quality of the clusters using silhouette scores.
#### Visualization: Using Seaborn and Matplotlib for data visualization (box plots, histograms, dendrograms).

### Technologies Used
#### Python: Core language for data manipulation and analysis.
#### Pandas: Used for data preprocessing, cleaning, and manipulation.
#### NumPy: Supports numerical computations.
#### Seaborn & Matplotlib: For creating insightful visualizations of the data.
#### SciPy: Used for hierarchical clustering and linkage methods.
#### Scikit-learn: Machine learning library for clustering, imputation, and evaluation metrics.
#### D-Tale: Interactive data exploration tool for analyzing the dataset.
#### Feature Engine: Outlier handling using Winsorization.

### Project Structure

#### plaintext
#### Copy code
#### University_Clustering_Project/
#### ├── data/
#### │   └── University_Clustering.xlsx    # Dataset used for clustering
#### ├── notebooks/
#### │   └── university_clustering.ipynb   # Jupyter Notebook for exploratory analysis and clustering
#### ├── src/
#### │   └── preprocessing.py              # Python scripts for data preprocessing
#### │   └── clustering.py                 # Clustering logic and silhouette score evaluation
#### ├── static/
#### │   └── plots/                        # Folder containing generated plots (box plots, heatmaps)
#### ├── README.md                         # Project overview
#### └── requirements.txt                  # Python dependencies

### Key Steps
#### 1. Data Preprocessing
#### Handling Missing Values: Using SimpleImputer and RandomSampleImputer to fill missing values in columns like SAT and graduation rates.
#### Data Normalization: Normalizing the numerical features before clustering to standardize the range of variables.
#### One-Hot Encoding: Encoding categorical variables such as university state to prepare the data for analysis.
#### 2. Outlier Detection and Treatment
#### Winsorization is applied to key variables (SAT, Top10, Accept, SFRatio) to cap outliers and ensure data consistency.
#### 3. Clustering
#### Dendrogram Plot: Hierarchical clustering is visualized using dendrograms, allowing us to determine the optimal number of clusters.
#### Agglomerative Clustering: The dataset is clustered into 3 groups based on the dendrogram results.
#### 4. Cluster Evaluation
#### Silhouette Score: A silhouette score is calculated to evaluate the performance and separation of the clusters.

#### Visualizing Results
#### Dendrogram and box plots are generated for analyzing the clusters.
#### Correlation heatmaps provide insights into relationships between features.
### Results
#### After clustering, each university is assigned to one of three clusters.
#### The clusters are analyzed based on key features, and their means and variances are compared.
#### Visualizations such as dendrograms, box plots, and heatmaps help interpret the clustering results.
### Conclusion
#### This project successfully demonstrates how to cluster universities using hierarchical clustering techniques. The results provide insights into how universities can be grouped based on similarities in their characteristics.
