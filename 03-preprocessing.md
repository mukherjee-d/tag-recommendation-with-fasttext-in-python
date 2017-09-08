# Pre-processing

With all the requirements out of the way, now it's time to jump into the fun stuff! 
As touched upon earlier, the major drawback found in FastText is that it does not perform pre-processing on your dataset. But thankfully, this is not very hard to achieve and in fact, allows room for experimentation, as will be discussed ahead.

## Required format
FastText requires the input data to be a text file with observations on each row. These observations must be of the following form- 
```
__label__text
```
This can be achieved using some simple string manipulation by appending the label before the content. The label refers to the category that the content is classified into. You can include multiple labels. 
```
test_data = []
for observation in file:
  string_to_save = u''
  for label in observation.labels():
    string_to_save += '__label__' + label + ' '
    string_to_save += observation
    test_data_list.append(string_to_save)
```
`test_data` will be your valid training set.

Additionally, you must ensure that there is no punctutation included in the content. Punctuation can be easily removed using regular expressions.
```
import re
re.sub(r'[^\w\s]',' ',content)
```
## Options
While you don't essentially __need__ to do any other pre-processing steps, cleaning the data further proves to often be very beneficial in bringing up your scores for recall and precision.
While playing around with FastText, the following proved useful-

### Removal of stop words
```
content = [w for w in output if w not in stopwords.words('english')]
```

### Using a POS tagger to only consider Nouns
```
from nltk import word_tokenize, pos_tag
nouns = [token for token, pos in pos_tag(word_tokenize(content)) if pos.startswith('N')]
```

### Stemming
```
content = stemmer.stemWords(output)
```
