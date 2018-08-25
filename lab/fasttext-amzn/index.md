# Sentiment Analysis on Amazon Reviews with fastText

We start with a dataset of a few million Amazon reviews in the fastText format.

`__label__<X> __label__<Y> ... <Text>`


For example:

` __label__positive The book was really exciting, top read for the year!`


In this case, the classes are `__label__1` and `__label__2`, and there is only one class per row.


`__label__1` corresponds to 1- and 2-star reviews, and `__label__2` corresponds to 4- and 5-star reviews. 
