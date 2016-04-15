"""
Pig Latin is a game of alterations played on the English language game. To create the Pig Latin form of an English word
the initial consonant sound is transposed to the end of the word and an ay is affixed (Ex.: "banana" would yield
anana-bay).
"""

import string

def isconsonant(letter):
    "Checks if a given letter is a consonant"

    if letter not in 'AEIOUaeiou':
        return True
    else:
        return False

def remove(givenlist,index):

    givenlist = givenlist[:index] + givenlist[index+1:]

    return givenlist

def ayyy(givenlist):

    new_list = givenlist[:] + ['a','y']

    return new_list

def piglatin(string):

    letter_list = list(string)

    for i in range(len(string)):
        if isconsonant(string[i]):
            neo_list = remove(letter_list,i)
            neo_list = neo_list[:] + ['-',string[i]]
            break

    ayyy_list = ayyy(neo_list)

    stringify = ''.join(str(e) for e in ayyy_list)

    return stringify
