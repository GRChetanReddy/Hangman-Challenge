#The Hangman Challenge
##The Game
The rules of the hangman game are as following:
A word is decided upon but is not revealed to the player except its length.
The player is supposed to guess the letters one by one, the player can wrongly guess 6 times(in our case). 
Upon guessing a letter correctly, its position and frequency in the word is revealed.

##My Approach
I have decided to use a small scale GPT model to solve this problem. Let's call our model the HM-GPT(Hangman-GPT). HM-GPT guesses a letter given an input of an unknown word represented by underscores and spaces. The model is trained on preprocessed data(described in next section). The model is trained for xx epochs, the first 30 epochs were trained at a learning rate of 310-3, then at a rate of 310-4 for 7 epochs with a decay rate of 0.001. The Adam optimizer was used during the training. The decision to change the lr was taken observing plateauing of loss over many iterations. The training was done on Kaggle and Google collab, then the weights of the model are loaded for prediction during the game. Given an initial input of underscores, we clean the word of spaces and pad the word with ‘*’ to adjust the word’s length to 29 (Reason for this explained in the data pre-processing section).  The model predicts the probability of each letter’s occurrence at each position. The letter with the maximum probability is the guess of the model that is submitted. 

##Data pre-processing
A dataset of 250k words is provided for training. We replace all the letters randomly from a word with ‘_’. Given an input like that, the model is supposed to predict the whole word during the training. The maximum length of a word in the dataset was found to be 29, hence the all the words were padded on the right by ‘*’ to match this length. The whole data was used to train the model. The testing of its accuracy was done by playing the hangman game through the given notebook.   
