# University Clustering Project
#### 1. Introduction
This project demonstrates how to perform hierarchical clustering on a university dataset. The dataset contains various attributes of universities, and we aim to apply data preprocessing, imputation techniques, outlier treatment, and clustering to extract meaningful insights.

#### 2. Dataset
The dataset used for this project is named University_Clustering.xlsx, and it contains information about several universities such as:

SAT Scores
Top 10% of High School Students Admitted
Acceptance Rate
Student-Faculty Ratio
Graduation Rate
#### Loading the Data
python
Copy code
import pandas as pd

#### Load the dataset
df = pd.read_excel(r'C:\Users\Swapnil Mishra\Desktop\DS\Hierarchical Clustering\University_Clustering\University_Clustering.xlsx')
#### 3. Data Exploration
To get an understanding of the data, we explore key statistical properties like the mean, median, mode, variance, and standard deviation.

python
Copy code
### Numerical statistics
print(df.select_dtypes(include=[np.number]).mean())
print(df.select_dtypes(include=[np.number]).median())
print(df.select_dtypes(include=[np.number]).mode())
#### 4. Data Preprocessing
4.1 Data Cleaning
We remove unnecessary columns and handle duplicates.

python
Copy code
### Drop the UnivID column
df.drop(['UnivID'], axis=1, inplace=True)

### Remove duplicate rows
df = df.drop_duplicates()
4.2 Missing Value Imputation
Different imputation techniques are applied for handling missing data:

Mean Imputation for SAT scores
Median Imputation for Student-Faculty Ratio
Random Imputation for Graduation Rate
python
Copy code
from sklearn.impute import SimpleImputer
mean_imputer = SimpleImputer(missing_values=np.nan, strategy='mean')
df['SAT'] = pd.DataFrame(mean_imputer.fit_transform(df[['SAT']]))
#### 5. Outlier Detection and Treatment
Winsorization is applied to cap outliers using the Interquartile Range (IQR) method.

python
Copy code
from feature_engine.outliers import Winsorizer

### Apply Winsorization
winsor = Winsorizer(capping_method='iqr', tail='both', fold=1.5, variables=['SAT', 'Top10', 'Accept', 'SFRatio'])
df[['SAT', 'Top10', 'Accept', 'SFRatio']] = winsor.fit_transform(df[['SAT', 'Top10', 'Accept', 'SFRatio']])
#### 6. Exploratory Data Analysis (EDA)
Boxplots to visualize the distribution of numeric features.
Histograms and Quantile-Quantile (Q-Q) Plots to check for normality.
Correlation Matrix with a heatmap to understand relationships between variables.
python
Copy code
### Boxplot for numeric features
df_num.plot(kind='box', subplots=True, sharey=False, figsize=(10,6))
#### 7. Clustering
7.1 Data Normalization
Data normalization is done to scale the variables before applying clustering.

python
Copy code
def norm_func(i):
    return (i - i.min()) / (i.max() - i.min())

df_norm = norm_func(df.iloc[:, 1:])
7.2 Hierarchical Clustering
Using Ward's method, we plot a dendrogram and apply agglomerative clustering.

python
Copy code
from scipy.cluster.hierarchy import dendrogram, linkage

### Dendrogram
tree_plot = dendrogram(linkage(df_norm, method='ward'))
7.3 Cluster Assignment and Evaluation
Clusters are formed and silhouette scores are used to evaluate the quality of clustering.

python
Copy code
from sklearn.cluster import AgglomerativeClustering

### Apply Agglomerative Clustering
hc = AgglomerativeClustering(n_clusters=3, metric='euclidean', linkage='ward')
cluster_labels = hc.fit_predict(df_norm)
#### 8. Results and Visualization
Dendrogram for visualizing the hierarchical clustering process.
Boxplots for each cluster to analyze feature distributions.
Silhouette Score to measure clustering performance.
python
Copy code
import seaborn as sns

### Correlation heatmap
corrmatrix = df.corr()
sns.heatmap(corrmatrix, cmap='coolwarm', annot=True)
plt.show()
#### 9. Conclusion
This project demonstrated the application of hierarchical clustering on a university dataset. Through data preprocessing, outlier treatment, and visualization techniques, we successfully identified clusters of universities based on their attributes.

#### 10. Libraries Used
Pandas: Data manipulation and analysis
Numpy: Numerical computations
Seaborn/Matplotlib: Data visualization
Scikit-learn: Machine learning algorithms for imputation and clustering
Feature Engine: Outlier detection and Winsorization
SciPy: Hierarchical clustering methods
D-Tale: Interactive data exploration
