# k-Nearest_Neighbors

The attached R notebook includes classification techniques using the k-Nearest Neighbors (kNN) algorithm. For more testing on k-NN, please follow the link below to my Kaggle notebooks where I apply kNN classification to non-parametric datasets. 

https://www.kaggle.com/gianzlupko/notebooks

### Load Iris data set 
```r data(iris)

str(iris) 
table(iris$Species) 
head(iris) 

# mix up the rows of the data set 

set.seed(9850)
runif(5)
```
