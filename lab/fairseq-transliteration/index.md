# Transliteration with Fairseq

For this lab we use [Fairseq](https://facebook.ai/developers/tools/fairseq) and a dump of Wikipedia for a language in a non-Latin alphabet.

## Transliteration

In the transliteration task we take a string as input and return a string as output.

Like translation, it is not a 1:1 mapping but probabilistic - some characters or character combinations are overloaded - and would require real natural language understanding to do perfectly.

## About seq2seq

Sequence-to-sequence or seq2seq models are useful when both input and output are a string.

It can also be applied to other types of sequences, like DNA.

It is commonly used for translation, but also for tasks like grammar correction or question answering.


## About Fairseq

Fairseq is [FAIR's implementation of seq2seq using PyTorch](https://github.com/pytorch/fairseq).

It was originally built for sequences of `words` - it splits a string on `' '` to get a list.

It supports byte-pair encoding and has an attention mechanism, but requires a GPU.


## Generating the data



## Training


## Validating


