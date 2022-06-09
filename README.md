# TV Script Generation Project using LSTMs

Here is a super fun project. Using the [Seinfeld scripts dataset](https://www.kaggle.com/datasets/thec03u5/seinfeld-chronicles), we generated more scripts! 

## Pre-processing
For NLP projects, we mostly do not use the text data by itself but we process it and transform it into a format that neural networks can understand. Specifically, we first create a lookup table that maps unique words into numbers and vice versa. Then, we tokenize the input by removing all characters that are not alphanumeric. We then group the text into ```seq_length``` long words (that are represented by integers) and then split these words groups into batches so we can perform mini-batch updates during training. Now, we move on to implementing the network!

## Building the network

We use a long short term memory (LSTM) network for this task. Its architecture is given below:

![Alt text](nn.png?raw=true "Title")

The embedding layer is used to store embeddings of a fixed dictionary, which is in this case the lookup table we created. Then, we use an LSTM layer of 1024 hidden units. We also use a dropout layer to prevent overfitting. We train this model for 7 epochs. For hyperparameter selection, we used these two references as a guide: 
1. https://www.tensorflow.org/text/tutorials/text_generation
2. https://wandb.ai/borisd13/char-RNN/reports/Text-Generation-With-Sequence-Models--VmlldzoxMDk2Ng

## Script generation 

Finally, we use our trained model to generate a script. Given the prompt __george__, our model generated this script:
```george:(to george) i don't want you to take a bite, i'm not getting a little more.

george:(to elaine) hey, what are you talking about?

kramer:(looking at the door) well, i gotta do something about my son-- i'm not gonna be able to get away with this, i have never seen you.. i don't know.

jerry: well, i'm sure it is.

kramer: well, you know, i'm sure.

jerry: well, maybe.

kramer: yeah!

elaine: what?!?

george: what do you think?

jerry: well, i guess it's a little strange.

kramer:(to jerry) hey.

jerry:(startled) yeah.(to kramer) what are you doing?

elaine:(to elaine) i can't believe i got to talk about it.

george: i can't.

elaine:(to the waitress) excuse me, i'm sorry.

jerry: yeah, i know, i don't know if i can.

george: what are we gonna do? i can't do this!

jerry: you want to see me?

george: yes, i am.

jerry: you know, you know, you don't know, maybe you should get going.(elaine and jerry both move back to the booth)

kramer: hey, jerry. how you doin'?

jerry: oh, i'm going to hell.

george: what are you doing here?

jerry: i just don't know what the hell said i said.

george: well i don't think i'm going to get the job.

jerry: you don't think so?

kramer: i don't know.

jerry: what do you think?

george: well it's just a few things.

george:(to george) what about the money?

elaine:(to george, he gets up to leave) you know, this woman```

It might not be the most thrilling script ever, but at least it is gramatically correct! 
