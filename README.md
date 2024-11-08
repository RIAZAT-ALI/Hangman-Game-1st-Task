# Hangman-Game-1st-Task
This is 1st task of CODE ALPHA internship

import random

words = ["riazy", "mazhar", "science", "raham", "vikram", "janwery"]


# Function to pick a random word
def get_word():
    return random.choice(words)

def play_hangman():
    word = get_word()
    word_letters = set(word)
    guessed_letters = set()
    tries = 6

    print("Welcome to Hangman!")
    print(f"The word {len(word)} letters. Good luck!")


    while len(word_letters) > 0 and tries > 0:
        print(f"\nYou have {tries} tries left.")
        print("Guessed letters:", " ".join(guessed_letters))


        word_display = [letter if letter in guessed_letters else "_" for letter in word]
        print("Current word: ", " ".join(word_display))

        # Player guess
        guess = input("Guess  letter: ").lower()

        if guess in guessed_letters:
            print("You already guessed that letter. Try again.")
        elif guess in word_letters:
            guessed_letters.add(guess)
            word_letters.remove(guess)
            print(f"Good guess {guess} is in the word.")
        else:
            guessed_letters.add(guess)
            tries -= 1
            print(f"Incorrect guess. {guess} is not in the word.")


    if tries == 0:
        print(f"\nYou are run out of tries. The word was '{word}'. Better luck next time!")
    else:
        print(f"\nCongratulations! You've guessed the word '{word}' correctly!")


play_hangman()
