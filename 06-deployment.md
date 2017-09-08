# Deployment

Once the optimal value of the features have been decided, the same parameters are used to build the final model.
The only difference in this step lies in the fact that _all_ the data will be used to build the model.

```
fasttext.supervised(filename, 'model_name', lr = 0.070, epoch = 9000, word_ngrams = 2, neg = 10, bucket = 10000, thread= 32)
```
## Loading the model
The `.bin` file created in the previous step is loaded by the following command and stored in a variable named `classifier`-
```
classifier = fasttext.load_model('model_name.bin')
```

## Predicting
To get suggested tags for any new content, there must be a pre-processing step before it is fed into the model.
The steps that will go into pre-processing will depend on what functionalities were performed on the training data.
Essentially, we must get the new content in the form of the data that was used to train the model.
This would include, but not be limited to, puntuation removal, stop word removal, stemming, POS tagging, etc.

After the content has been cleaned, it is fed into the model using-
```
classifier.predict_proba(clean_content)
```
We can then store this in a variable called `label`. 
Slicing the first 5 indices of `label` using `label[:5]` will then give the top 5 tags suggested along with their probabilities of occurence. If less than 5 tags were predicted by the model, all of those will be spit out. The number of tags can be changed according to the needs of the project.

### Discarding tags with low probabilities
As an additional step, you can add functionality to remove any tag suggestions with very low probabilities. In the testing phase for my project, I found the cut-off to be `1.95313e-08`. This number can vary from case to case. But removing any labels that have probablities lower than that value bolstered the removal of many non-sensical tag recommendations. 
