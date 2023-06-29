import random as R
import time as T
import sys

def get_word(wordarr):
    with open("ting hangman.txt") as wordDB:
        for line in wordDB:
            i = line.split(" ")
            wordarr.append(i)
wordarr = []
var = get_word(wordarr)
print(wordarr)
#
#
#
##

def guessletter(word, guessword, lives):
    userguess = (input("please enter a letter")).upper()
    cnt = -1
    for char in word:
        cnt += 1
        if userguess == char:
            guessword[cnt] = userguess
    if userguess not in word:
         print(lives)
         lives = -1
         displayword(guessword, lives, word)
         return lives
     #
     #
     #

def displayword(guessword, lives, word):
    userreturn = ''.join([item for item in guessword])
    userreturn = userreturn.replace('[', ''). replace(']', '').replace('\'', '').replace(',','')
    print("Live remaning = ", lives )
    print(userreturn+'\n')
    if lives == 0:
        stringvar = 'Game Over!'
        print("\n\n")
        for i in range(0, len(stringvar)):
            print(stringvar[i], end='')
            T.sleep(0.2)
        print("\n\nword war:", word)
        sys.exit()
         #
         #
         #
         #
         #
         #
def main():
    wordarr, completearr = [], []
    get_word(wordarr)
    for i in range(0, len(wordarr)):
        for j in range(0, len(wordarr[i])):
            completearr.append(wordarr[i][j])
    invalidchar, removearr,guessword = [",", "\n", ".", ":", ";", "£", "$", "&", "/"], [],[]
    lives = 5
    for str in completearr:
        if len(str) < 5:
            removearr.append(str)
    else:
        for i in invalidchar:
            if i in str:
                removearr.append(str)
    word = completearr[R.randint(0, len(completearr))]
    word = word.upper()
    wordlength = len(word)
    for i in range(0, wordlength):
        guessword.append('_')
    print("\n")
    print(guessword)
    while '_' in guessword:
        lives = guessletter(word, guessword, lives)
        print(lives)
main()
