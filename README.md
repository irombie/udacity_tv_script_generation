# TV Script Generation Project using LSTMs

Here is a super fun project. Using the [Seinfeld scripts dataset](https://www.kaggle.com/datasets/thec03u5/seinfeld-chronicles), we generated more scripts! 

## Pre-processing
For NLP projects, we mostly do not use the text data by itself but we process it and transform it into a format that neural networks can understand. Specifically, we first create a lookup table that maps unique words into numbers and vice versa. Then, we tokenize the input by removing all characters that are not alphanumeric. We then group the text into ```seq_length``` long words (that are represented by integers) and then split these words groups into batches so we can perform mini-batch updates during training. Now, we move on to implementing the network!

# Building the network

We use a long short term memory (LSTM) network for this task. Its architecture is given below:

![Alt text](nn.png?raw=true "Title")


