# k-Nearest_Neighbors

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

# generate random numbers for number of rows in iris 
gp <- runif(nrow(iris)) 
gp

# put iris in order of gp, which was randomly generated with runif function
# specifiaclly in the subset brackets we use order on row but not on the iris columns 

iris <- iris[order(gp), ]
str(iris) 
head(iris) 


# rescale numerical features before using kNN 

str(iris)
# check range of variables in the iris field 
summary(iris[,c(1,2,3,4)]) 

# notice that especially the pedal width field has a much different range than the others 
# features with larger numbers would have an outsize affect on prediction 
# need to normalize the data - a popular way to rescale the ranges 
# create function to normalize 


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


# split data now that data was successfully normalized and dataset re-ordered
# split into train and test set 
# save at least 10% of observations for testing
# that would be about 15 since we have 150 total in iris 
# we save 20 here for test 
# first create training data set 
# below takes the first 129 rows for train and keeps all columns 


iris_train <- iris_norm[1:129, ]
iris_test <- iris_norm[130:150, ]


# next you need to set the target variable, the one you want to predict 
# these are Species for this study 
# we did not normalize the Species field so to access Species as our target variable 
# it is in the original data set
# create target variable vectors for both train and test
# they should be the same length as train and test respectively 

head(iris)
iris_train_target <- iris[1:129, 5]
iris_test_target <- iris[130:150, 5]

```
