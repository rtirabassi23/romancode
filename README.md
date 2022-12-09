# romancode
Roman's main repository
'''
Name: Roman Tirabassi
Date: 11/29/2022
Description: Tic Tac Toe Game

'''
from pickle import TRUE
theBoard = [ ['1','2','3'],      
            ['4', '5', '6'],            
            ['7', '8', '9'] ]





def printBoard():                                                               #This is represent the board in the computer
    print(theBoard[0][0] + '|' + theBoard[0][1] + '|' + theBoard[0][2])
    print('-+-+-')
    print(theBoard[1][0] + '|' + theBoard[1][1] + '|' + theBoard[1][2])
    print('-+-+-')
    print(theBoard[2][0] + '|' + theBoard[2][1] + '|' + theBoard[2][2])
    
    
def checkLocation(move, turn):	                         # This turns the user's input into a position on the board

    status = True

    if move == 1 and theBoard[0][0] == '1':
        
        theBoard[0][0] = turn
        
    elif move == 2 and theBoard[0][1] == '2':
        
        theBoard[0][1] = turn
        
    elif move == 3 and theBoard[0][2] == '3': 
        
        theBoard[0][2] = turn
        
    elif move == 4 and theBoard[1][0] == '4': 
        
        theBoard[1][0] = turn
        
    elif move == 5 and theBoard[1][1] == '5': 
        
        theBoard[1][1] = turn
        
    elif move == 6 and theBoard[1][2] == '6': 
        
        theBoard[1][2] = turn
        
    elif move == 7 and theBoard[2][0] == '7': 
        
        theBoard[2][0] = turn
        
    elif move == 8 and theBoard[2][1] == '8': 
        
        theBoard[2][1] = turn
        
    elif move == 9 and theBoard[2][2] == '9': 
        
        theBoard[2][2] = turn

    else:
        status = False
    return status
        
def checkWinner(turn):                                      	#This checks if the player has won the game by getting 3 in a row
    
    winner = False

    
    if theBoard[0][0] == turn and theBoard[0][1] == turn and theBoard[0][2] == turn: #top across
        print(turn + " Wins!")
        winner = True
        
    elif theBoard[1][0] == turn and theBoard[1][1] == turn and theBoard[1][2] == turn: #middle across
        print(turn + " Wins!")
        winner = True
        
    elif theBoard[2][0] == turn and theBoard[2][1] == turn and theBoard[2][2] == turn:  #bottom across
        print(turn + " Wins!")
        winner = True
        
    elif theBoard[0][0] == turn and theBoard[1][1] == turn and theBoard[2][2] == turn:  #diagonal down right
        print(turn + " Wins!")
        winner = True
        
    elif theBoard[0][2] == turn and theBoard[1][1] == turn and theBoard[2][0] == turn: #diagonal down left
        print(turn + " Wins!") 
        winner = True
        
    elif theBoard[0][0] == turn and theBoard[1][0] == turn and theBoard[2][0] == turn: #vertical left
        print(turn + " Wins!")
        winner = True
        
    elif theBoard[0][1] == turn and theBoard[1][1] == turn and theBoard[2][1] == turn: #vertical middle
        print(turn + " Wins!")
        winner = True
        
    elif theBoard[0][2] == turn and theBoard[1][2] == turn and theBoard[2][2] == turn: #vertical right
        print(turn + " Wins!")
        winner = True

    return winner




def main():

    turn = 'X'
    count = 0

    

    while count < 9:
        
        printBoard()                                        #This prints the board so players can see where they position their player
        print("\n")

        move = int(input("It's your go," + turn + " move to which spot? count is: " + str(count))) 
        
        status = checkLocation(move, turn)
        
        if status == True:
            pass
        else:
            print("This space is taken, please take another spot.")
            continue
        
        winner = checkWinner(turn)
        
        if winner == True:                                                      #This checks if the winner is true and also prints that they won
            print("Congrats" + ' ' + turn + ' ' + "won\n\n\n")
            printBoard()
            break
        
        count = count + 1                                                       #Adds to the count of the game. It goes up to 9 turns
   
        
   
        turn = 'O'
             
        if count == 9:                                                          #If all turns are used and there is no winner then it's a tie and count would be 9
            print("tie!!!\n\n\n")
            printBoard()
            return
        printBoard()
        print("\n")
        
        move = int(input("It's your go," + turn + " move to which spot? count is: " + str(count)))
        
        
        o_go = True
        while o_go == True:
        
            if checkLocation(move, turn) == False:
                continue 
            else: 
                o_go = False 
        
        o_go = True
                                                                                #Creates the winner if they get 3 in a row                
        winner = checkWinner(turn)
   
        if winner == True:
            print("Congrats" + ' ' + turn + ' ' + "won\n\n\n")                  
            printBoard()
            break     
    
        turn = 'X'                                                              #Goes back to X's turn and then it will create a loop
        
        count = count + 1
        
        
        '''
        if count > 8:
            print("Game Over.")                
            print("It's a Tie.")
            break
        '''
        
if __name__ == "__main__":
    main()
