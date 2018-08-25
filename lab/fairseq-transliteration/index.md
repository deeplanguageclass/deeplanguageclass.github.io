# Transliteration with Fairseq

*For this lab we use our [character-level fork of Fairseq](https://github.com/deeplanguageclass/fairseq-transliteration).  You can do this lab with the [IPython Notebook](https://github.com/deeplanguageclass/fairseq-transliteration.ipynb) on Google Colab.  The full dataset is in the repo [fairseq-transliteration-data](https://github.com/deeplanguageclass/fairseq-transliteration-data).  A demo serving a trained model is up at [104.155.65.42:5007/translit](http://104.155.65.42:5007/translit).*

For this lab we use [Fairseq](https://facebook.ai/developers/tools/fairseq) for transliteration by generating data from a dump of Wikipedia for a language in a non-Latin alphabet.

## Transliteration

Today's text data are full of informal or otherwise lossy or inconsisten Latinisations (Romanisations) of non-Latin text, for example Russian [translit](https://en.wikipedia.org/wiki/Informal_romanizations_of_Cyrillic#Translit), Chinese [pinyin](https://en.wikipedia.org/wiki/Pinyin), Arabic [arabizi](https://en.wikipedia.org/wiki/Arabic_chat_alphabet), Persian [Pingilish](https://en.wikipedia.org/wiki/Romanization_of_Persian#ASCII_Internet_romanizations) and similar for many other languages like Hindi, Greek or Armenian.

Transliteration is the task of converting text to the canonical alphabet, for example Russian to proper Russian Cyrillic.  Both the input an output are a string.

Like translation, it is not a 1:1 mapping but probabilistic - some characters or character combinations are overloaded - and would require real natural language understanding to do perfectly.

One of the first open-source deep learning approaches to transliteration is [translit-rnn by YerevaNN](https://github.com/YerevaNN/translit-rnn/).  In their blog post [*Automatic transliteration with LSTM*](http://yerevann.github.io/2016/09/09/automatic-transliteration-with-lstm/) they give examples.


## seq2seq

Sequence-to-sequence or seq2seq models are useful when both input and output are a string.

It can also be applied to other types of sequences, like DNA.

seq2seq is commonly used for translation, but is also useful for tasks like summarisation, grammar correction or question answering.


## Fairseq

Fairseq is [FAIR's implementation of seq2seq using PyTorch](https://github.com/pytorch/fairseq).

It was originally built for sequences of `words` - it splits a string on `' '` to get a list.

It supports byte-pair encoding and has an attention mechanism, but requires a GPU.

## Character-level

Word-level seq2seq will not be very efficient for transliteration, because it would not handle words not seen in training.  Therefore in [our fork of Fairseq](https://github.com/deeplanguageclass/fairseq-transliteration) we made a [change to split on every character instead of on `' '`](https://github.com/deeplanguageclass/fairseq-transliteration/commit/c201085e9c88ccf3706fc9ef06ab131782e3ae53).

## Generating the data

We take YerevaNN's approach of generating the "translit" data with the mappings in [fairseq-transliteration-data/transliteration.json](https://github.com/deeplanguageclass/fairseq-transliteration-data/blob/master/transliteration.json).

## Training

Because we need a GPU, we put the [IPython Notebook](https://github.com/deeplanguageclass/fairseq-transliteration.ipynb) Google Colab.  Fairseq supports checkpointing, so you can test the model at any epoch and continue training.

## Demo

There is a demo online at [104.155.65.42:5007/translit](http://104.155.65.42:5007/translit) that serves a model with Flask.  The model was trained for about an hour (three epochs) on a laptop.
