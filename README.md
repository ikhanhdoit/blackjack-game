# 2 players should be able to play the game (both sitting at the same computer)
# The board should be printed out every time a player makes a move
# You should be able to accept input of the player position and then place a symbol on the board

# to take input from a user:
# player1 = input("please pick a marker 'X' or 'O'")

# if you need an integer value, use:
# position = int(input('Please enter a number'))

# to clear the screen between moves:
# from IPython.display import clear_output
# print('\n'*100)

from IPython.display import clear_output

# showing display board
def display_board(board):
    print('\n'*100)
    print('   |   |')
    print(' ' + board[7] + ' | ' + board[8] + ' | ' + board[9])
    print('   |   |')
    print('---+---+---')
    print('   |   |')
    print(' ' + board[4] + ' | ' + board[5] + ' | ' + board[6])
    print('   |   |')
    print('---+---+---')
    print('   |   |')
    print(' ' + board[1] + ' | ' + board[2] + ' | ' + board[3])
    print('   |   |')

# board = []
test_board = ['#','1','2','3','4','5','6','7','8','9']
# isplay_board(board)

def player_input():
    marker = ''
    #KEEP ASKING PLAYER1 to choose X or O
    while marker != 'X' and marker != 'O':
        marker = input("Player 1, choose X or O: ").upper()
    
    #ASSIGN PLAYER 2, the opposite marker
    player1 = marker
    
    if player1 == 'X':
        player2 = 'O'
    elif player1 == 'O':
        player2 = 'X'
    return (player1, player2)

# player1_marker, player2_marker = player_input() is used for output

# Write a function which takes an input marker string 'X' or "O' and a given number and stores it to a list at that appendix.
# Write a function that takes in the board list object, a market(X or O), and desired position (1-9) and assigns it to the board
def place_marker(board, marker, position):
    board[position] = marker

# Win tic tac toe?
# 789, 456, 123 , 741, 852, 963, 753, or 159
def win_check(board, mark):
    return ((board[1] == mark and board[2] == mark and board[3] == mark) or 
            (board[4] == mark and board[5] == mark and board[6] == mark) or 
            (board[7] == mark and board[8] == mark and board[9] == mark) or 
            (board[7] == mark and board[4] == mark and board[1] == mark) or 
            (board[8] == mark and board[5] == mark and board[2] == mark) or 
            (board[9] == mark and board[6] == mark and board[3] == mark) or 
            (board[7] == mark and board[5] == mark and board[3] == mark) or 
            (board[1] == mark and board[5] == mark and board[9] == mark))

import random

# randomize who goes first with random.randint()
def choose_first():
    random_start = random.randint(0,1)
    if random_start == 0:
        return 'Player 1 will start this round'
    else:
        return 'Player 2 will start this round'

# function that shows if the board space is free
def space_check(board, position):
    
    return board[position] == ' '

# check if board is full
def full_board_check(board):
    i = ' '
    for i in range(1,10):
        if space_check(board, int(i)):
            return False
    # board is full if we return true    
    else: 
        return True

# player choosing next space
def player_choice(board):
    position = 0
    # asks for players next position (1-9)
    # then uses space_check function to see if it's a free position
    while position not in [1,2,3,4,5,6,7,8,9] or not space_check(board, position):
        try:
            position = int(input('Choose a position: (1-9) '))
        except ValueError:
            print('Sorry. Please choose a position between 1-9:  ')
    # then return position for later use
    return position

# want to replay?
def replay():
        chance = input('Play again? Enter Yes or No ').lower()
        return chance.startswith('y')

display_board(test_board)
print('Welcome to Tic Tac Toe!')
print('Above are the numerical positions. Remember them carefully!')

while True:
    # Set the game up here
    the_board = [' '] * 10
    player1_marker, player2_marker = player_input()
    turn = choose_first()
    print(turn)
    play_game = input('Ready to play? Yes or No? ').lower()````
    if play_game.startswith('y'):
        game_on = True
    else:
        game_on = False

    while game_on:
        #Player 1 Turn
        if turn == 'player1':
            display_board(the_board)
            print('Player 1:')
            position = player_choice(the_board)
            place_marker(the_board, player1_marker, position)
        
            if win_check(the_board, player1_marker):
                display_board(the_board)
                print('Player 1 has won the game')
                game_on = False
            else:
                if full_board_check(the_board):
                    display_board(the_board)
                    print('The game is a tie')
                    game_on = False
                else:
                    turn = 'player2'
                    
        else:
            # Player2's Turn
            display_board(the_board)
            print('Player 2:')
            position = player_choice(the_board)
            place_marker(the_board, player2_marker, position)

            if win_check(the_board, player2_marker):
                display_board(the_board)
                print('Player 2 has won the game')
                game_on = False
            else:
                if full_board_check(the_board):
                    display_board(the_board)
                    print('The game is a tie')
                    game_on = False
                else:
                    turn = 'player1'
                    
                    
    if not replay():
        break
    
