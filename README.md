# Tic_Tac_Toe
A game that can be played by two users

import random

def print_board(board):
	
	print('	'+board[1]+' '+'|'+' '+board[2]+' '+'|'+' '+board[3]+' ')
	print('	'+'----------')
	print('	'+board[4]+' '+'|'+' '+board[5]+' '+'|'+' '+board[7]+' ')
	print('	'+'----------')
	print('	'+board[7]+' '+'|'+' '+board[8]+' '+'|'+' '+board[9]+' ')

def player_input():
	marker=''
	while not (marker == 'X' or marker == 'O'):
		marker = input('Player 1 choose between X or O')
	if marker == 'X':
		return('X','O')
	else:
		return('O','X')

def place_marker(board,marker,position):
	board[position]=marker

def win_check(board,mark):
	return((board[1]==board[2]==board[3]==mark) or
	(board[4]==board[5]==board[6]==mark) or
	(board[7]==board[8]==board[9]==mark) or
	(board[1]==board[4]==board[7]==mark) or
	(board[2]==board[5]==board[8]==mark) or
	(board[3]==board[6]==board[9]==mark) or
	(board[1]==board[5]==board[9]==mark) or
	(board[3]==board[5]==board[7]==mark))

def choose_first():
	flip=random.randint(0,1)
	if flip == 0:
		return 'Player 1'
	else:
		return 'Player 2'

def space_check(board,position):
	return board[position]==' '

def full_board(board):
	for i in range(1,10):
		if(space_check(board,i)):
			return False
	else:
		return True

def player_choice(board):
	
	position = 0
	
	while position not in [1,2,3,4,5,6,7,8,9] or not space_check(board,position):
		position = int(input('Choose a position from (1-9) '))

	return position

def replay():
	choice = input ('Play Again ? Yes or No')
	return choice =='Yes'

#While loop to keep running game
print('Welcome to TIC TAC TOE')

while True:
	#Play the game
	#Set EveryThing up
	the_board = [' ']*10
	player1_marker,player2_marker = player_input()
	turn = choose_first()
	print(turn +' will go first')
	play_game = input(' Ready to play ? y/n ')
	if play_game=='y':
		game_on=True
	else:
		game_on=False
	while game_on:
		if turn=='Player 1':
			print_board(the_board)
			position=player_choice(the_board)
			place_marker(the_board,player1_marker,position)
			print_board(the_board)
			if(win_check(the_board,player1_marker)):
				
				print('Player 1 has WON !!!!!!!')
				game_on=False
			else:
				if(full_board(the_board)):
					print_board(the_board)
					print('It is a TIE')
					break
				else:
					turn = 'Player 2'
		else:
			print_board(the_board)
			position=player_choice(the_board)
			place_marker(the_board,player2_marker,position)
			if(win_check(the_board,player2_marker)):
				print_board(the_board)
				print('Player 2 has WON !!!!!!!')
				game_on=False
			else:
				if(full_board(the_board)):
					print_board(the_board)
					print('It is a TIE')
					break
				else:
					turn = 'Player 1'

	if not replay():
		break



#def choose_player(m)

board = ['#','1','2','3','4','5','6','7','8','9']
print_board(board)
