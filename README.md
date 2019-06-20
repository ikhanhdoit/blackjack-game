#Create a deck of 52 cards
import random

suites = ("Hearts", "Diamonds", "Spades", "Clubs")
ranks = ('Two', 'Three', 'Four', 'Five', 'Six', 'Seven', 'Eight', 'Nine', 'Ten', 'Jack', 'Queen', 'King', 'Ace')
values = {'Two':2, 'Three':3, 'Four':4, 'Five':5, 'Six':6, 'Seven':7, 'Eight':8, 'Nine':9, 'Ten':10, 'Jack':10,
         'Queen':10, 'King':10, 'Ace':11}

while True:
    playing = True
    break

#Shuffle the deck

class Deck:
    def __init__(self, suit, rank))
    self.suit = suit
    self.rank = rank
    

#Ask the Player for their bet
#Make sure that the Player's bet does not exceed their available chips
#Deal two cards to the Dealer and two cards to the Player
#Show only one of the Dealer's cards, the other remains hidden
#Show both of the Player's cards
#Ask the Player if they wish to Hit, and take another card
#If the Player's hand doesn't Bust (go over 21), ask if they'd like to Hit again.
#If a Player Stands, play the Dealer's hand. The dealer will always Hit until the Dealer's value meets or exceeds 17
#Determine the winner and adjust the Player's chips accordingly
#Ask the Player if they'd like to play again
