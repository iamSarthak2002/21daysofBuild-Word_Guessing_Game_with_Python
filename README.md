Introduction
One popular game is where we guess an unknown word or phrase one letter at a time. If the player(s) can guess the word within a certain amount of attempts, they will win. Alternatively, when they run out of attempts, they will lose. This game is usually played on paper, but what if we could make it using Python?

In this project tutorial, we'll be using:

The random module
A code editor (VS Code, Codédex Build, etc.)
Create the Word Bank
First, we'll need to create a word bank of all the possible words to be guessed, and randomly select one to be the correct answer. This way, the game has an element of mystery and surprise! 🔍🕵

We can do this by installing the random module:

import random
Next, we will make a list that has all the possible words that can be the answer. This tutorial will only use five words, but you can add as many as you want!

word_bank = ['rizz', 'ohio', 'sigma', 'tiktok', 'skibidi']
Now, we will randomly choose one of these words to be the correct answer. 🎲

word = random.choice(word_bank)
The random.choice() method is used to randomly select a word from the word_bank list and to assign it to the word variable. All possible options have an equal probability of being chosen.

Finishing the Setup
We don't want to reveal the letters of the word we're trying to guess initially, so we need a list of underscores as "placeholders" to represent letters that haven't been guessed yet. The number of placeholders should directly correspond with the number of letters the word has. (i.e., the word “apple” is five letters, so there should be five underscores as placeholders)

guessedWord = ['_'] * len(word)
In Python, you can multiply a list by an integer and the list will repeat that amount of times. The ['_'] creates a list with a single underscore element, while the len(word) function returns the length (or number of characters) in the word string.

We'll finish setting by determining how many attempts the player has at guessing the word. We will be using 10 for this tutorial, but you can make it any number you want.

attempts = 10
Go ahead and save the file and let's move on to the game loop!

Game Loop
We need to create a while loop so the player can continuously guess until they run out of attempts or guess the word correctly. 🔁

while attempts > 0:
Each time the loop runs, we will display the current state of the word being guessed.

while attempts > 0:
  print('\nCurrent word: ' + ' '.join(guessedWord))
The statement is printed on a new line via \n, and joins the strings in guessedWord together with spaces. For example, if the state of guessedWord is ['a', '_', 'p', '_', 'e'], the result would be the string "a _ p _ e", making the program look smoother and less clunky.

Since the guessing is based on user input, we need to prompt the user to guess a letter and store it in a variable.

guess = input('Guess a letter: ')
We then need to determine whether or not the guessed letter is in the correct word. If it is, we loop through each letter of the word to find which position the letter is in and replace the placeholder with the guessed letter.

if guess in word:
  for i in range(len(word)):
    if word[i] == guess:
      guessedWord[i] = guess
  print('Great guess!')
The for loop goes over each index of the word, to check every letter. If the letter at position i matches the player’s guess, it updates the position in the guessedWord list. We'll print out some positive feedback to let the user know that they guessed correctly.

Furthermore, we need to write some code that handles situations where the user guesses incorrectly. If the player's guess is not in the word, the number of attempts decreases by one. Since attempts is an integer, we must also convert it to a string to let the player know how many attempts they have left.

else:
  attempts -= 1
  print('Wrong guess! Attempts left: ' + str(attempts))
We're almost done! We'll know if the player has won the game when they guess all the letters in the word. If there are no more underscores as placeholders in the guessedWord variable, there are no more blanks left. When the player wins, we will break the while loop and end the game.

  if '_' not in guessedWord:
        print('\nCongratulations!! You guessed the word: ' + word)
        break
Finally, we need a condition that results in a loss for the player when they run out of attempts and reveal the correct word.

else:
    print('\nYou\'ve run out of attempts! The word was: ' + word)
Note: We don't need to break the while loop because the condition was while attempts > 0.

When you're finished, the game loop should look something like this:

while attempts > 0:
   
    print('\nCurrent word: ' + ' '.join(guessedWord))

    guess = input('Guess a letter: ').lower()
   
    if guess in word:
        for i in range(len(word)):
            if word[i] == guess:
                guessedWord[i] = guess
        print('Great guess!')
    else:
        attempts -= 1
        print('Wrong guess! Attempts left: ' + str(attempts))
    if '_' not in guessedWord:
        print('\nCongratulations!! You guessed the word: ' + word)
        break
    else:
      print('\nYou\'ve run out of attempts! The word was: ' + word)
Conclusion
Congratulations! You have completed the project! 🎉🎊

In this tutorial, you used the following to build a word-guessing game:

The random module
List and string operations
Input/output handling
Control flow statements
Now, you can enjoy this game you built yourself, or with friends!

More Resources
Source Code
Random Module Documentation
