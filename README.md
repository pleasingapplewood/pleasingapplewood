def checkwin():
    if square[1] == square[2] == square[3]:
        return 1
    elif square[4] == square[5] == square[6]:
        return 1
    elif square[7] == square[8] == square[9]:
        return 1
    elif square[1] == square[4] == square[7]:
        return 1
    elif square[2] == square[5] == square[8]:
        return 1
    elif square[3] == square[6] == square[9]:
        return 1
    elif square[1] == square[5] == square[9]:
        return 1
    elif square[3] == square[5] == square[7]:
        return 1
    elif all(cell != str(cell) for cell in square[1:10]):
        return 0
    else:
        return -1


def board():
    print("\n\n\tTic Tac Toe\n\n")
    print("Player 1 (X)  -  Player 2 (O)\n\n")
    print(f"     |     |     \n  {square[1]}  |  {square[2]}  |  {square[3]}\n_____|_____|_____\n     |     |     \n  {square[4]}  |  {square[5]}  |  {square[6]}\n_____|_____|_____\n     |     |     \n  {square[7]}  |  {square[8]}  |  {square[9]}\n     |     |     \n")


square = ['o', '1', '2', '3', '4', '5', '6', '7', '8', '9']
player = 1

while True:
    board()
    player = 1 if player % 2 else 2
    print(f"Player {player}, enter a number:  ", end="")
    choice = int(input())
    mark = 'X' if player == 1 else 'O'

    if 1 <= choice <= 9 and square[choice] == str(choice):
        square[choice] = mark
    else:
        print("Invalid move ")
        player -= 1

    result = checkwin()
    player += 1

    if result == 1:
        board()
        print(f"==>Player {player - 1} win ")
        break
    elif result == 0:
        board()
        print("==>Game draw")
        break
