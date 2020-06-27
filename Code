import itertools
from colorama import Fore, Back, Style,init
init()
#Horizontal win
def win(current_game):

	def all_same(l):
		if l.count(l[0]) == len(l) and l[0] != 0:
			return True
		else:
			return False

	#Horizontal Winner		
	for row in game:
		print(row)
		if all_same(row):
			print(f"Player {row[0]} is the winner horizontally!!")
			return True

	#Vertical winner
	for col in range(len(game)):
		check=[]
		for row in game:
			check.append(row[col])
		if all_same(check):
			print(f"Player {check[0]} is the winner Vertically !!")
			return True	
 	#Diagonal winner		
	diags=[]

	for col,row in enumerate(reversed(range(len(game)))):
		diags.append(game[row][col])
	if all_same(diags):
			print(f"Player {diags[0]} is the winner Diagonally(/)!!")
			return True
	

	diags=[]
	for ix in range(len(game)):
		diags.append(game[ix][ix])
	if all_same(diags):
			print(f"Player {diags[0]} is the winner Diagonally (\\)!!")
			return True
	
	return False

def game_board(game,player=0,row=0,col=0,just_val=False):
	try:
		if game[row][col] != 0:
			print("!This place has already been taken try another!")
			return game,False
		print("   "+"  ".join([str(i) for i in range(len(game))]))		
		if not just_val:
			game[row][col]=player
		for count, row in enumerate(game):
			colored_row = ""
			for item in row:
				if item == 0:
					colored_row += "   "
				elif item == 1:
					colored_row += Fore.GREEN + ' X ' + Style.RESET_ALL
				elif item == 2:
					colored_row += Fore.MAGENTA + ' O ' + Style.RESET_ALL	
			print(count, colored_row)	
		return game , True

	except IndexError as e:
		print("Error:input correct index value!!", e)	
		return game,False
	except Exception as e:
		print("Something went horribally wrong!!",e)	
		return game,False

play=True
player=[1,2]
while play:
	game_size = int(input("What size of game would you like to play?:"))
	game = [[0 for i in range(game_size)]for i in range(game_size)]
	game_won=False
	game , _ =game_board(game,just_val=True)
	player_choice = itertools.cycle([1,2]) 
	while not game_won:
		curr_player = next(player_choice)
		print(f"Current player:{curr_player}")

		played = False

		while not played:
			col_choice = int(input("What coloumn do you wish to enter (0,1,2)?: "))
			row_choice = int(input("What row do you wish to enter (0,1,2)?: "))
			game,played=game_board(game, curr_player, row_choice, col_choice)

		if win(game):
			game_won=True
			again=input("The curret game is over, do you wish to play again (y/n):")
			if again.lower() == "y":
				print("Restarting....")
			elif again.lower() == "n" :
				print("Byee!")
				play= False
			else:
				print("Wrong entry!!")
				play= False
