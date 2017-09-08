# Testing
With our training set ready, we move on to building the model and test.

## Building the model
```
classifier = fasttext.supervised('training_set.txt', 'test_model', lr = 0.075, epoch = 10000, word_ngrams = 2, neg = 10, bucket = 10000, thread= 32)
```
## K-Fold Cross Validation
```
random.shuffle(data) #Shuffles data to ensure maximum randomness
test_data = data[int(float(k)/10*len(data)):int(float(k+1)/10*len(data))] #Divides 1/10th of the data as test data
train_data = [x for x in data if x not in test_data] #Divides 9/10th of the data as training data
```
## Getting Recall and Precision
```
result = classifier.test('testing_set.txt', k = 5)
result.recall
result.precision
```
