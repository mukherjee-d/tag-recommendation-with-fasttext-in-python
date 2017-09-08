# Prerequisites 

Make sure your system is running a version of Python that is 2.7 or newer. While not necessary, it is useful to have pip installed to ensure easy installation of all the packages that are needed.

The most important library that needs to be downloaded-
* [fasttext](https://pypi.python.org/pypi/fasttext/0.8.3) 0.8.3
This supports Python 2.6 or newer. Additionally, it requires-
* [Cython](https://pypi.python.org/pypi/Cython/) 0.26.1 to build the C++ extension. Make sure to install Cython before you install fasttext. 

While the FastText library provides a very efficient learning model that can be trained, it does not ensure an end-to-end process. 
We still need to rely on additional libraries to perform pre-processing on the data. For pre-processing, the following libraries are needed- 
* [NLTK](https://pypi.python.org/pypi/nltk/3.2.4) 3.2.4
* [SnowballStemmer](https://pypi.python.org/pypi/snowballstemmer) 1.2.1
