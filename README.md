# CryptoClustering
Python and unsupervised learning to predict if cryptocurrencies are affected by 24-hour or 7-day price changes

Unsupervised learning is a class of machine learning (ML) techniques used to find patterns in data. The data given to unsupervised algorithms is not labelled, which means only the input variables (x) are given with no corresponding output variables. In unsupervised learning, the algorithms are left to discover interesting structures in the data on their own.

Unsupervised learning is a machine learning algorithm that searches for previously unknown patterns within unlabeled data sets. The most prominent methods of unsupervised learning are cluster analysis and principal component analysis.

In this challenge, I use knowledge of Python and unsupervised learning to predict if cryptocurrencies are affected by 24-hour or 7-day price changes.
1.     Importing Libraries:

    import pandas as pd:  It provides data structures like DataFrames that allow for easy handling and manipulation of structured data.

    import hvplot.pandas: hvPlot simplifies the process of creating visualizations from Pandas DataFrames.

    from sklearn.cluster import KMeans: KMeans is a clustering algorithm that groups data points into clusters based on their similarities.

    from sklearn.decomposition import PCA:  PCA is a technique used for dimensionality reduction, reducing the number of features while preserving the most important information in the data.

    from sklearn.preprocessing import StandardScaler: Standardization scales the data to have zero mean and unit variance, which can improve the performance of some algorithms.
2.  Load the data into a Pandas DataFrame
3. Generate summary statistics
4. Visualisation data 
    hvplot.line:     The line function is used to create line plots.

    Parameters:

    width=800: This sets the width of the plot to 800 pixels, adjusting its size horizontally. 

    height=400: This sets the height of the plot to 400 pixels, adjusting its size vertically. 

    rot=90: This parameter adjusts the rotation angle of the x-axis labels (the tick labels) by 90 degrees. 

5. Normalize the data from the CSV file 
The variable scaled_data now contains the normalized data after applying the StandardScaler. Each column in the DataFrame df_market_data has been standardized, and the result is stored in scaled_data. This new dataset has the same shape as the original df_market_data, but the values have been transformed to have a mean of 0 and a standard deviation of 1.
6. Create Data frame with the scaled data.
 New DataFrame called df_market_data_scaled is created to store the scaled data obtained from applying the StandardScaler() to the df_market_data DataFrame.
 The scaled data obtained from applying the StandardScaler() is used to create the new DataFrame, df_market_data_scaled. Each column of the original DataFrame df_market_data is now scaled to have a mean of 0 and a standard deviation of 1.
 The original index of df_market_data likely contains the names of cryptocurrencies. The code copies these names to the new DataFrame df_market_data_scaled by creating a new column named "coin_id".
 The "coin_id" column is set as the new index of the DataFrame, replacing the default numerical index. This change is made to use the cryptocurrency names as the unique identifiers for each row.
 After the above operations, the DataFrame df_market_data_scaled contains the scaled data with cryptocurrency names as the index. The code snippet displays the first few rows of the DataFrame using the head() function to provide a sample of the scaled data.
 The describe() function provides statistical summaries of the scaled data. It includes statistics such as count, mean, standard deviation, minimum, 25th percentile, median (50th percentile), 75th percentile, and maximum for each column. This summary provides insights into the distribution and variability of the scaled data.
 7. Visualisation with df_market_data_scaled.hvplot.line
 8. Creates a list of k-values ranging from 1 to 11 using the range() function and then converts it to a Python list using the list() function. The range(1, 12) function generates a sequence of numbers starting from 1 up to (but not including) 12. So, it will create the numbers 1, 2, 3, ..., 11.
 The list() function is used to convert the range object into a Python list. The resulting list, k_values_list, contains the values from 1 to 11.
 9. Create an empty list to store the inertia values
 10. Create the loop. After running the loop, the inertia list will contain the inertia values computed for each value of k. The inertia list will have 11 elements, corresponding to the 11 values of k from 1 to 11.
 11. Creates a dictionary named dic_inertia to store the data needed to plot the Elbow curve. It then converts this dictionary into a DataFrame named inertia_df, which can be used for visualization and further analysis.
 12. Python

inertia_df['inertia_fraction_with_respect_to_one_cluster'] = inertia_df['inertia'] / inertia_df.iloc[0, 1]

This line of code calculates the fraction of inertia for each value of k (number of clusters) with respect to the inertia value obtained when k=1 (i.e., one cluster). It normalizes the inertia values by dividing them by the inertia at k=1.
The calculation inertia_df['inertia_fraction_with_respect_to_one_cluster'] - inertia_df['inertia_fraction_with_respect_to_one_cluster'].shift() performs the element-wise subtraction between the current inertia fraction and the inertia fraction from the previous row. This results in the inertia rate of decrease for each k value, which represents the change in inertia fraction from one level to the next.

By adding the 'inertia_rate_of_decrease' column to inertia_df, the DataFrame now contains valuable information about how the inertia changes as the number of clusters (k) increases, helping to identify potential "elbow" points in the Elbow curve. These elbow points can provide insights into the optimal number of clusters for the data.
13. Plot a line chart with all the inertia values 
14. Create a dictionary with the data to plot the Elbow curve
    Create a DataFrame with the data to plot the Elbow curve
15. Plot a line chart with all the inertia values computed with the different values of k to visually identify the optimal value for k.
17. Initialise the K-Means model using the best value for k and fit the K-Means model using the scaled data
18. Predict the clusters to group the cryptocurrencies using the scaled data
19. Create a scatter plot using hvPlot by setting 
pca = PCA(n_components=3)
20. Use the PCA model with `fit_transform` to reduce to three principal components.
21. Visualise and compare the resultz. 


