# Twenty-One-game
Twenty one if your sum &lt;= 21 you win
The game randomly distributes the player's and computer's numbers
Then the sum comparison begins
Then the player is asked if he wants to draw an additional number or not
If the player's total is less than 21, he can draw a card whenever he wants
The computer also draws a card as long as his total is less than 17
Then the winner is determined. If your total is greater than 21 or less than the computer's total, you lose, And vice versa

Note
The number 1, 11 are considered if one number appears in the player's or computer's cards and the total of these cards is less than 11, then 1 is replaced with 11 and the sum is repeated.

Then the comparison is done again to determine the player

import os
import time
import random

def clear():
    os.system("cls" if os.name == "nt" else "clear")



list_number = [1,2,3,4,5,6,7,8,9,10,10,10,10]
player = []
computer = []

def random_choose():
    global list_number
    global player
    player = random.choices(list_number,k = 2)
    for i in range(len(player)):
        if player[i] == 1 and sum(player) < 11:
            player[i] = 11
    


def random_computer():
    global list_number
    global computer
    computer = random.choices(list_number, k = 2)
    for i in range(len(computer)):
        if computer[i] == 1 and sum(computer) < 11:
            computer[i] = 11
    if sum(computer) < 17:
        computer.append(random.randint(1,10))



def check_Win():
    global list_number
    global computer
    
        
    if sum(player) <= 21 and sum(computer) >= 21:
        print("Computer went over 21, you win 🌟")
    elif sum(player) > sum(computer) and sum(player) <= 21:
        print("You win 🎉")
    elif sum(player) == sum(computer) and sum(player) <= 21:
        print("Draw 😅")
    else:
        print("You losse! 👎")

    
while True:
    clear()
    start = input("""Choose a game to start.......\n
1. Froggy
2. Twenty one
3. Snake
--------------
""").capitalize()  

    clear() 

    if start == "Twenty one":
        print("Starting game........")
        time.sleep(2)
        clear()
        print("""
 ______               __                     
/_  ___    _____ ___ / /___ __  ___  ___ ___ 
 / / | |/|/ / -_/ _ / __/ // / / _ \/ _ / -_)
/_/  |__,__/\__/_//_\__/\_, /  \___/_//_\__/ 
                       /___/                 
""")
        
        random_choose()
        random_computer()
        while True:
            print(f"Your cards are {player}, current scour is {sum(player)}")
            print(f"Computer's first card is {computer[0]}\n\n")
            time.sleep(1)

        
            if input("Get another card? (y/n) ") == "n":
                print(f"Your final hand: {player} with score {sum(player)}")
                print(f"computer's final hand : {computer} with score {sum(computer)}")
                check_Win()
                time.sleep(5)
                break
            
   
            else:
                player.append(random.randint(1,10))
    else:
        break
