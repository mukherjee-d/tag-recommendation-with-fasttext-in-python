# Testing
With our model built in the last step, we need to verify it against a test set and measure the values of precision@k and recall@k to get an idea of how well our model is performing. While there are many ways to perform validation of your model, this tutorial will focus on k-fold cross-validation. Another method that is definitely suggested to look into is bootstrapping.

## K-Fold Cross Validation
With K-fold cross validation, you divide your dataset into k folds. Over k iterations, (k-1) folds of the data are used for training and the kth fold is used for testing. This ensures that all of our data is used (k-1) times for building the model and at least one time for validating the built model. Doing so makes us certain that our test set is representative of our true data.
To perform this on the dataset, to ensure maximum randomness, we shuffle the data first.
```
random.shuffle(data)
```
K-fold cross validation is usually performed with either 3, 5 or 10 folds. In this tutorial, we will follow it for 10 folds-
```
for k in range(0, 9):
  test_data = data[int(float(k)/10*len(data)):int(float(k+1)/10*len(data))] #Divides 1/10th of the data as test data
  train_data = [x for x in data if x not in test_data] #Divides 9/10th of the data as training data
```
Save both the test_date and train_data as temporary `.txt` files in each step.

## Getting Recall and Precision
For each of these 10 iterations, build the classifier with the specified params with the training set and run the classifier against the test set. This is done by using the following command-
```
result = classifier.test('testing_set.txt', k = 5)
```
The value of k specifies the value for recall@k and precision@k. This is not to be confused with the k-fold cross-validation.
The tutorial sticks with using the values @5. 
Recall and precision measure the true positive rate and positive predictive value respectively. There is always a trade-off between precision and recall in any solution. Depending on your problem at hand, you should focus on optimizing one of them. 

To get the value of recall, use `result.recall` and the value of precision can be found by `result.precision`. Averaging these values over all the iterations will give you an overall picture of how the model works as a whole.
