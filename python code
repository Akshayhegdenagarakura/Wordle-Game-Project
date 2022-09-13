from termcolor import colored  # for coloring the letters
import random  # to pick the random word


# the function to pick the random words from list file "words.txt",
# and it returns the randomly picked word
def read_random_word(file_name):
    file = open(file_name)
    words = file.readlines()
    file.close()
    return random.choice(words)  # return the random picked word from text the file


# main function
print("\n")
print("------****** Welcome to Wordle ******------")
play_again = ""
while play_again != "exit":  # type exit to exit the game after 6 attempts or after winning the game
    print("Type a 5 letter word and hit Enter.\n You have 6 trials to guess the word in the game.\n")
    score = 0  # initializing score to 0
    word = read_random_word("words.txt")  # returned word from the function read_random_word()
    # print(word)
    for attempt in range(1, 7):
        guess = input().lower()  # considering all the input letters as lowercase letters
        if guess == "exit":
            break
        m = len(guess)  # length of the guessed word
        n = len(word)  # length of the original word
        word1 = word  # initializing original word to word1
        if m > n:
            q = n
        else:
            q = m
        c = [0, 0, 0, 0, 0]  # to print letters in colour
        for i in range(min(q, 5)):
            for j in range(q):
                if word1[j] == guess[i] and i == j:  # if the letter in the guessed word letter in exact position
                    c[i] = 1  # initialize the value of that position to 1
                    word1 = word1[0:i] + '0' + word1[i + 1:]  # by slicing word1 we can nullify the string
                    break
        for i in range(min(q, 5)):
            if c[i] == 0:
                for j in range(q):
                    if word1[j] == guess[i]:  # if guessed word letter in original word but not in position
                        c[i] = 2  # initialize that position in list c as 2
                        break

        count = 0
        for p in range(min(len(c), 5)):
            if c[p] == 1:
                count += 1
        if count == len(c):
            score += 1  # if all letters exactly match with original letters of word print in win and score
            print(colored(f"Congratulations! You guessed the word in {attempt} guess and your score is {score}.",
                          'blue'))
            break

        for a in range(min(len(guess), 5)):
            if c[a] == 1:  # if it detects 1 in list c , it will print it in color green
                print(colored(guess[a], 'green'), end="")
            elif c[a] == 2:  # if it detects 2 in list c , it will print it in color yellow
                print(colored(guess[a], 'yellow'), end="")
            elif c[a] == 0:  # otherwise print in white
                print(guess[a], end="")

        print()
        print(f"You have {6 - attempt} to guess the word ")  # for remaindering how many attempts left
        print("*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*")

        if attempt == 6:  # if the attempts exceeds 6 , break the for loop and lose the game.
            score = 0  # and show the original word.
            print(colored(f"You didn't guess the word within 6 tries, it was {word}", 'red'))

    # to play again hit enter else type exit
    play_again = input(colored(f"To continue the game press Enter or Type 'exit' for quit the game\n", 'magenta'))
