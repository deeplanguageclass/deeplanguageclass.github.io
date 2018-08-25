# Classifying Amazon reviews with fastText

*You can do this lab on your own Unix machine, in [IPython Notebook on Google Colab] (https://colab.research.google.com/drive/1yelP5eE0lIMXQaXeOq5vlnOby99VAUnz) or on [Kaggle](https://www.kaggle.com/bittlingmayer/amazonreviews/home).*

For this lab we will use the [fastText](https://github.com/facebookresearch/fastText) library from FAIR for training word2vec models and a classifier.

We will use a dataset of [4M Amazon reviews labelled by sentiment in the fastText format](https://www.kaggle.com/bittlingmayer/amazonreviews/home). 

### Labelling

1- and 2-star reviews we consider to have negative sentiment, 4- and 5-star reviews positive sentiment.

We just throw away 3-star reviews.

## Dataset

The dataset is already split into train and test files in the fastText format.

`__label__<X> __label__<Y> ... <Text>`


For example:

` __label__positive The book was really exciting, top read for the year!`


In this case, the classes are `__label__1` and `__label__2`, and there is only one class per row.


`__label__1` corresponds to 1- and 2-star reviews, and `__label__2` corresponds to 4- and 5-star reviews. 


## Download the data

```
wget https://storage.googleapis.com/amazonreviews/train.ft.txt.bz2
wget https://storage.googleapis.com/amazonreviews/test.ft.txt.bz2
bzip2 -d train.ft.txt.bz2
bzip2 -d test.ft.txt.bz2
```
Now do `head` or `tail` to see a few rows.

## Install fastText


## Train

```
./fasttext supervised -input train.ft.txt -output model_amzn
```

## Test

```
./fasttext test model_amzn.bin test.ft.txt
```

## Parameters

