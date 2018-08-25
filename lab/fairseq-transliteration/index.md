# Transliteration with Fairseq

For this lab we use [Fairseq](https://facebook.ai/developers/tools/fairseq) and a dump of Wikipedia for a language in a non-Latin alphabet.

## Transliteration

In the transliteration task we take a string as input and return a string as output.

Like translation, it is not a 1:1 mapping but probabilistic - some characters or character combinations are overloaded - and would require real natural language understanding to do perfectly.

One of the first open-source deep learning approaches to transliteration is [translit-rnn by YerevaNN](https://github.com/YerevaNN/translit-rnn/).

In their blog post[*Automatic transliteration with LSTM*](http://yerevann.github.io/2016/09/09/automatic-transliteration-with-lstm/) they give examples.


## seq2seq

Sequence-to-sequence or seq2seq models are useful when both input and output are a string.

It can also be applied to other types of sequences, like DNA.

It is commonly used for translation, but also for tasks like grammar correction or question answering.


## Fairseq

Fairseq is [FAIR's implementation of seq2seq using PyTorch](https://github.com/pytorch/fairseq).

It was originally built for sequences of `words` - it splits a string on `' '` to get a list.

It supports byte-pair encoding and has an attention mechanism, but requires a GPU.

## Character-level

Word-level seq2seq will not be very efficient for transliteration, because it would not handle words not seen in training.  Therefore in [our fork of Fairseq](https://github.com/deeplanguageclass/fairseq-transliteration) we made a [change to split on every character instead of on `' '`](https://github.com/deeplanguageclass/fairseq-transliteration/commit/c201085e9c88ccf3706fc9ef06ab131782e3ae53).

## Generating the data

We take YerevaNN's approach of generating the "translit" data with the mappings in [fairseq-transliteration-data/transliteration.json](https://github.com/deeplanguageclass/fairseq-transliteration-data/blob/master/transliteration.json).

## Training

Because we need a GPU, we put the [IPython Notebook](https://github.com/deeplanguageclass/fairseq-transliteration.ipynb) Google Colab.

