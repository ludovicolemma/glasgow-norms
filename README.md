# The Project
This is my first python and data mining comprehensive project. The objective was to apply and explore some fundamental concepts I studied. The tasks I focused on were Data Understanding, Data Preparation, Clustering, Classification, and Pattern Mining. I wrote about the processes and results of these tasks in a final report called "Glasgow_Norms_Report.pdf" which I compiled with LaTex. The files "\*-notebook.ipynb" are the refined and reduced versions of the Jupyter Notebooks of the work I've done divided by task.

<p align="center">
<a href="https://github.com/ludovicolemma/glasgow-norms/blob/main/Glasgow_Norms_Report.pdf">Read the Report</a> •
<a href="https://github.com/ludovicolemma/glasgow-norms/blob/main/dataset.csv">View the Dataset</a></br></br>
<a href="https://github.com/ludovicolemma/glasgow-norms/blob/main/understanding-preparation-notebook.ipynb">Data Understanding and Preparation Code</a> •
</p>

# The Glasgow Norms
The Glasgow Norms are a set of ratings for English words on nine psycholinguistic dimensions: arousal, valence, dominance, concreteness, imageability, familiarity, age of acquisition, semantic size, and gender association. Three other variables are included in the dataset I worked on, namely length, polysemy, and the frequency of the word (in the Google Newspapers Corpus). </br>
There were originally two sets of words, one of 808 words, the other of 4800 words, which then were merged for this study. The experiment was run online (via the University of Glasgow's [platform](https://participants.psy.gla.ac.uk/)), each participant rated a list of either 101 (from 8 possible lists of the 808 word set) or 150 words (from 32 possible lists of the 4,800 word set).

# Summary of the Project

- [Data Understanding and Preparation](https://github.com/ludovicolemma/glasgow-norms/blob/main/understanding-preparation-notebook.ipynb)
  * Data semantics and data description: Here I provide a brief description of some particularities of the features of the dataset, namely which are the shortest and longest words, the number of polysemous and non-polysemous words, the most and least frequent words, and the scale of the features and its meaning
  * Distribution of the variables and statistics: Here I provide some histograms, scatterplots, density, and line plots of the distribution of the length and polysemy of the words across other features.
  * Data quality and variable transformations: Here I evidenced the missing values while filling them, then I presented the number of outliers computed from the box plot and the reasoning of the log-transformation of the variable "frequency" and some plots to relate it to polysemy
  * Highly correlated variables: Here I studied the most correlated variables and I evidenced some particular information about their distributions across the variable "gender" (discretized) through histograms, scatterplots, and density plots
  * Feature selection: Here I provided the process I followed to select the features, preliminarily I applied the variance inflation factor, then I did a principal component analysis, I explained why I focused on three principal components through a screeplot, and I characterized them explaining their loadings
- Clustering
  * Clustering analysis by k-means: Here I explained the results obtained by applying k-means with the process of hyperparameter selection through SSE and the aggregated Silhouette Score
  * Analysis by density-based clustering: Here I explained why DBSCAN didn't work, the hyperparameter selection process, and the comparison of the resulting noise to the previously identified outliers 
  * Analysis by hierarchical clustering: Here I studied the differences between four different linkage criteria of the agglomerative hierarchical clustering algorithm through dendrograms, I compared the resulting clusters by measuring how much they captured polysemous words and how much they differed and why I concluded the average linkage criterion was the best with this dataset
  * Comparison of the three clustering algorithms: Here I compared the results of k-means and hierarchical clustering algorithms through a silhouette analysis of the clusters and by measuring how much the clusters captured the polysemous words
- Classification: Preliminarily I explained why I didn't use the PCA for this task, how I divided the training and test set and how I balanced the polysemous and non-polysemous classes through a random undersampling on the training set, in fact, the polysemy of the words was the target variable of the task
  * Decision tree algorithm: Here I studied how to build the model, I explained how I set the parameters of the decision tree through a gridsearch with k-fold cross-validation, I presented the ROC Curve and PR Curve and I evidenced some thresholds to compare some resulting metrics of the respective confusion matrices
  * Knn algorithm: Here I explained how I applied KNN, from the selection of the k parameter with a gridsearch and the analysis of the resulting performances as before comparing multiple thresholds (*I didn't understand properly KNN at the time of writing, as such I only applied the algorithm knowing generally what was written in the sklearn documentation, and in the report I may have used "model" improperly*) 
  * Performance comparison of the two models: Finally I compared the performances I obtained and evidenced the best classificator
- Pattern Mining: Preliminarily I explained which features I discretized and how I determined their intervals
  * Frequent pattern extraction: Firstly I presented through a graph which percentage of support I adopted to determine the threshold to look for frequent itemset with the apriori algorithm, in particular how I focused on maximal frequent itemsets and the resulting frequent patterns containing polysemy
  * Association rules extraction: Here I presented how I extracted various association rules looking through different levels of confidence
  * Application of the extracted rules: Finally I used some of the extracted rules to predict the "polysemy" and "high frequency" of the words, comparing the results to the performance of the KNN algorithm at 0.5 threshold
