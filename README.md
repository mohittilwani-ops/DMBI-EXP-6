DMBI Experiment 6 – Bank Customer Churn System
Experiment Title
To Implement a Clustering Algorithm Using Python – Bank Customer Churn System (K-Means Clustering)
Aim
To implement the K-Means clustering algorithm using Python on the Bank Customer Churn System dataset and analyze the customer groups formed.
Theory
Clustering
Clustering is an unsupervised machine learning technique used to group similar data points based on their characteristics. It discovers patterns and natural structures in data without using predefined class labels. Similarity is commonly measured using distance measures such as Euclidean distance.
Types of Clustering
1. Hard Clustering: Each data point belongs to exactly one cluster. The groups are distinct and easy to interpret.
2. Soft Clustering: A data point can belong to multiple clusters with different membership probabilities or degrees.
K-Means Clustering
K-Means is an unsupervised algorithm that divides data into a predefined number K of clusters. It assigns each data point to the nearest centroid and repeatedly updates the centroids until the assignments stabilize. It aims to minimize the within-cluster sum of squared distances.

Uses: Customer segmentation, grouping similar records, pattern discovery, image compression, and preliminary anomaly detection.
Elbow Method
The Elbow Method plots inertia for different K values. The bend in the curve indicates a possible balance between cluster compactness and the number of clusters.
Evaluation Measures
- Silhouette Score: Evaluates cluster separation and cohesion. A higher value generally indicates better separation.
- Inertia: Measures the sum of squared distances from points to their assigned centroids. It generally decreases as K increases.
- Davies-Bouldin Index: Compares within-cluster scatter with separation between clusters. A lower value generally indicates better-separated, more compact clusters.
Dataset Information
- Dataset name: Bank Customer Churn
- Input file: Churn_Modelling.csv
- Number of records: 10,000
- Original attributes: 14
- Selected clustering features: 8 numerical attributes
- Excluded identifiers: RowNumber, CustomerId, and Surname
- Target attribute: Exited (used only after clustering for interpretation)
The selected numerical attributes are CreditScore, Age, Tenure, Balance, NumOfProducts, HasCrCard, IsActiveMember, and EstimatedSalary.

Important: Exited is not used to train K-Means because K-Means is unsupervised. It is used only after clustering to examine the churn distribution within each cluster.
Software Required
- Python 3
- Google Colab, Jupyter Notebook, or VS Code
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
Files
- bank_customer_churn_system_exp6.py – Complete Python implementation.
- Churn_Modelling.csv – Input dataset; keep it in the same folder for local execution.
- bank_customer_churn_clustered_data.csv – Generated dataset with cluster labels.
- bank_customer_churn_cluster_means.csv – Mean values of selected features for each cluster.
- bank_customer_churn_cluster_churn_profile.csv – Post-clustering stayed/exited percentage by cluster.
Implementation Steps
1. Load dataset: Read Churn_Modelling.csv using Pandas and display its shape, columns, first five records, and missing-value counts.
2. Select features: Select the eight numerical customer attributes listed above. Fill missing numerical values using the median, if required.
3. Standardize features: Apply StandardScaler so features are on a comparable scale. This matters because K-Means uses distance calculations and large-scale attributes could otherwise dominate.
4. Plot Elbow Method: Fit K-Means for K values from 2 through 10, record inertia, and plot K against inertia.
5. Apply K-Means: Choose K by inspecting the elbow graph. The supplied practical uses optimal_k = 4 as a starting choice; change it if the generated graph indicates another value. Fit K-Means and assign a cluster label to every record.
6. Evaluate clusters: Calculate Silhouette Score, Inertia, and Davies-Bouldin Index.
7. Visualize clusters: Create a scatter plot using Age on the x-axis and Balance on the y-axis, with points coloured by cluster. The model itself uses all eight selected features, not just Age and Balance.
8. Analyze cluster characteristics: Calculate the mean of the selected features for each cluster. Then use Exited only after clustering to calculate the percentage of stayed and exited customers within each cluster.
How to Run
Install the required libraries
pip install pandas numpy matplotlib seaborn scikit-learn
Run locally
1. Put Churn_Modelling.csv in the same folder as bank_customer_churn_system_exp6.py.
2. Run:
python bank_customer_churn_system_exp6.py
Run in Google Colab
Run the Python file's code in a Colab notebook. The script detects Colab and opens a file-upload prompt. Upload Churn_Modelling.csv.
Results Shown in the Supplied Experiment PDF
The supplied PDF shows an example run with:
- K = 4
- Cluster 0: 2,474 records
- Cluster 1: 2,428 records
- Cluster 2: 2,899 records
- Cluster 3: 2,199 records
- Silhouette Score: 0.1222
- Inertia: 58292.87
- Davies-Bouldin Index: 2.076
The PDF's cluster-wise churn profile is:
Cluster	Stayed (%)	Exited (%)
0	84.48	15.52
1	67.92	32.08
2	80.06	19.94
3	86.54	13.46


These are the example values visible in the supplied PDF. Your run can differ if the dataset or software environment differs. The PDF itself says to inspect the Elbow graph and not assume the elbow must always be at K = 4.
Understanding the Visualizations and Output
- The Elbow graph compares inertia across K values; select K near the point where inertia reduction begins to slow.
- The Age vs Balance scatter plot is a two-dimensional view of clusters. K-Means was fitted using all eight selected features, so overlap in this plot does not necessarily mean the full clusters are identical.
- Cluster-wise averages describe the customer profiles represented by each group.
- The churn profile helps identify whether some groups contain a higher proportion of exited customers. Since Exited is excluded from the clustering inputs, it does not influence cluster formation.
Result
K-Means clustering was implemented using Python on the Bank Customer Churn System dataset. Numerical customer attributes were selected and standardized before applying the algorithm. The Elbow Method was used to inspect a suitable number of clusters. The resulting clusters were evaluated using the Silhouette Score, Inertia, and Davies-Bouldin Index, and visualized using a scatter plot. Cluster-wise averages and the post-clustering churn distribution were examined to understand the customer profiles.
Conclusion
The experiment demonstrates how K-Means can group bank customers based on similarities in their numerical demographic, financial, and account-activity attributes. The cluster evaluation measures and cluster profiles help interpret the resulting customer segments. The churn attribute is examined only after clustering and is not used to form the clusters.
