# Training
With our training set ready, we move on to training the model.

## Building the model
The command used to build the supervised model using fasttext is-
```
fasttext.supervised(params)
```
The following paramters are required-
```
input_file             training file path
output                 output file path 
```
The input is the `.txt` file specified in the last step and the output file is a binary file which will hold the trained model.

The following additional parameters can also be specified (the defaults are mentioned in the brackets)-
```
label_prefix           label prefix ['__label__']
lr                     learning rate [0.1]
lr_update_rate         change the rate of updates for the learning rate [100]
dim                    size of word vectors [100]
ws                     size of the context window [5]
epoch                  number of epochs [5]
min_count              minimal number of word occurences [1]
neg                    number of negatives sampled [5]
word_ngrams            max length of word ngram [1]
loss                   loss function {ns, hs, softmax} [softmax]
bucket                 number of buckets [0]
minn                   min length of char ngram [0]
maxn                   max length of char ngram [0]
thread                 number of threads [12]
t                      sampling threshold [0.0001]
silent                 disable the log output from the C++ extension [1]
encoding               specify input_file encoding [utf-8]
pretrained_vectors     pretrained word vectors (.vec file) for supervised learning []
```
### Tips from practice-
After rigorously testing the supervised model against different values of the optional parameters, not surprisingly the learning rate (`lr`) and the number of epochs (`epoch`) stood out. They seem to have an inverse relationship with each other. Very low values of `lr` (<= 0.50) seemed to give the best values of predictions with high values of `epoch` (>=10000) and vice-versa. 

### Word of caution-
Do not tweak the value of `thread` to be more than your CPU's internal thread count. 
