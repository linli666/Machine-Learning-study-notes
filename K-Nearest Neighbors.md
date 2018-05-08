# K-NN (K-Nearest Neighbors)
##
The K-Nearest Neighbors algorithm can be used for classification and regression. For now, I focus on classification. K-NN classifier is memory based supervised learning, which means it memorize all the labeled examples in the training set and then use those memorized examples to classify new object later.   
1. What K means?  
K is how many number of nearest points you want to use to do predict. Typically, the value of K is an odd number. When K is greater than 1, we use simple majority vote to decide which class the new object belongs to.
(To find the best value of K, we can write a for loop for multiple K values.)
2. Decision Boundary  
The decision boundary is excactly halfway between two points for different classes.

### Four things to specify before using K-NN algorithm
1. Distance Metric  
Euclidean distance or simple straight line to measure the distance between points. The most common distance metric and the one that scikit-learn uses by default is the euclidean instead of straight line distance. 
2. The number of K nearest neighbors  
The value of K is at least 1 and typically an odd number.  
3.Optional weighting function on the nearest neighbors points  
Some cases, you may want to give some neighbors more influence on the outcome. It's optional.
4. Method for aggregating the classed of nearest neighbors points  
Typically use simple majority vote.

### Steps of Applying K-NN in Python 
Here I use scikit-learn library to apply the K-NN algorightm. scikit-learn library can take pandas dataframe and numpy array.   
1. libraries Preparation 
```
from sklearn.model_selection import train_test_split
from sklearn.neighbors import KNeighborsClassifier
```
2. Split the dataset into X_train, y_train, X_test, y_test
```
X = df[[features_names]]
y = df[target]
X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=0)
```
3. Specify the value of K and fit the KNeighborsClassifier
```
knn = KNeighborsClassifier(n_neighbors = 5)
knn.fit(X_train, y_train)
```
4. Predict on new object or test data
```
knn.predict([[values of features]])
knn.predict(X_test)
```
5. Estimate the accuracy on test data (The value of score should be a float between 0 and 1)
```
accuracy = knn.score(X_test, y_test)
```
