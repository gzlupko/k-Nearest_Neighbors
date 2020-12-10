# k-Nearest_Neighbors

### sample branch from master 

The attached R notebook includes classification techniques using the k-Nearest Neighbors (kNN) algorithm. For more testing on k-NN, please follow the link below to my Kaggle notebooks where I apply kNN classification to solve domain-specific challenges. 

https://www.kaggle.com/gianzlupko/notebooks

### Load and pre-process data 
```r data(iris)

str(iris) 
table(iris$Species) 
head(iris) 

# mix up the rows of the data set 

set.seed(9850)
runif(5)
gp <- runif(nrow(iris)) 
gp


iris <- iris[order(gp), ]
str(iris) 
head(iris) 

str(iris)
# check range of variables in the iris field 
summary(iris[,c(1,2,3,4)]) 


normalize <- function(x) { 
  return( (x-min(x)) / (max(x) - min(x) ) ) } 

# check normalize on a range of numbers 
normalize(c(1,2,3,4,5))
normalize(c(10, 20, 30, 40, 50)) 
normalize(c(1, 40, 70, 100, 300))


# now use normalize function on iris' variables 


iris_norm <- as.data.frame(lapply(iris[,c(1,2,3,4)], normalize))

# check that the variable ranges have been normalized 
str(iris_norm)
summary(iris_norm)


iris_train <- iris_norm[1:129, ]
iris_test <- iris_norm[130:150, ]

head(iris)
iris_train_target <- iris[1:129, 5]
iris_test_target <- iris[130:150, 5]

```
