"""
Python Web Development Techdegree
Project 1 - Number Guessing Game
--------------------------------

For this first project we will be using Workspaces.

NOTE: If you strongly prefer to work locally on your own computer, you can totally do that by clicking: File -> Download Workspace in the file menu after you fork the snapshot of this workspace.

"""


"""Psuedo-code Hints

When the program starts, we want to:
------------------------------------
1. Display an intro/welcome message to the player.
2. Store a random number as the answer/solution.
3. Continuously prompt the player for a guess.
  a. If the guess greater than the solution, display to the player "It's lower".
  b. If the guess is less than the solution, display to the player "It's higher".

4. Once the guess is correct, stop looping, inform the user they "Got it"
     and show how many attempts it took them to get the correct number.
5. Let the player know the game is ending, or something that indicates the game is over.

( You can add more features/enhancements if you'd like to. )
"""
# write your code inside this function.
import random
import time


high_score = 100
def start_game():
    global high_score
    print("-----------------------------------------------------------------------------")
    print("Hello! Welcome to the number guessing game!")
    print("The current high score for this session is... {}".format(high_score))
    time.sleep(2.5)
    winning_number = random.randint(1,10)
    print("The game is quite simple! I have chosen a number between 1 and 10.")
    time.sleep(2.5)
    print("When you guess, I will tell you if it is higher, or lower. Let's get started!")
    time.sleep(2.5)

    guesses = 1
    while True:

            try:
                guess = int(input("Please guess a number between 1 and 10:  "))
                if guess > 10 or guess <= 0:
                    raise ValueError

            except ValueError as err:
                print("Input must be a number between 1 and 10")
            else:

                if guess > winning_number:
                    guesses = guesses + 1
                    print("Lower!")
                    continue

                elif guess < winning_number:
                    guesses = guesses + 1
                    print("Higher!")
                    continue

                elif guess == winning_number:
                    print("You guessed correctly! The winning number was {}!".format(str(winning_number)))
                    time.sleep(2.5)
                    print("It took you", guesses,"guesses!")
                    if guesses <  high_score:
                        high_score = guesses
                    time.sleep(2.5)
                    while True:

                        try:
                            replay = input("Type YES to replay, or type NO to quit.  ")
                            replay = replay.upper()
                            if replay != "YES" and replay != "NO":
                                raise ValueError

                        except ValueError as err:
                            print("You must either type YES to replay or NO to quit.  ")

                        else:

                            if replay == "YES":
                                start_game()
                            elif replay == "NO":
                                exit()



if __name__ == '__main__':
    # Kick off the program by calling the start_game function.
    start_game()
