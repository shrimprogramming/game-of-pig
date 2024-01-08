import random


total = 0
turns = 0
turn_score = 0

comp_total = 0
comp_turns = 0
comp_turn_score = 0


class color:
    BLUE = '\033[94m'
    RED = '\033[91m'
    BOLD = '\033[1m'
    UL = '\033[4m'
    END = '\033[0m'

while total < 20: 
    print (color.RED + color.BOLD + color.UL + "Turn score: " + str(turn_score) + 
    color.END + color.RED + " | " + color.UL + "Score: " + str(total) + color.END + 
    color.RED + " | " + color.UL + "Turns: " + str(turns) + color.END)
    
    print (color.BLUE + color.BOLD + color.UL + "Computer turn score: " + str(comp_turn_score) + color.END 
    + color.BLUE + " | " + color.UL + "Computer score: " 
    + str(comp_total) + color.END + color.BLUE + " | " + color.UL +
    "Computer turns: " + str(comp_turns) + color.END)
    
    com = input(color.BOLD + "Would you like to roll or bank?" + color.UL + "(NO CAPS)" 
    + color.END + " ")
    
    if com == "roll":
        roll = random.randint(1, 6)
        print ("You rolled a " + str(roll) + ".")
        if roll == 1:
            print (color.BOLD + "Start over." + color.END)
            turn_score = 0
            turns = turns + 1
        else:
            turn_score = turn_score + roll
    elif com == "bank":
        print ("You banked.")
        total = total + turn_score
        turn_score = 0
        turns = turns + 1
        
    if comp_turn_score == 0:
        roll = random.randint(1,6)
        print("Computer rolled a " + str(roll)+ ".")
        if roll == 1:
            print (color.BOLD + "Computer rolled a 1. Starting over." + color.END)
            comp_turn_score = 0
            comp_turns = comp_turns + 1
            
            
    comp_choice = random.randint(1,2)
    if comp_choice == 1:
        roll = random.randint(1,6)
        print ("Computer rolled a " + str(roll) + ".")
        if roll == 1:
            print (color.BOLD + "Computer rolled a 1. Starting over." + color.END)
            comp_turn_score = 0
            comp_turns = comp_turns + 1
            if comp_turn_score == 0:
                roll = random.rantint(1,6)
                print("Computer rolled a " + str(roll))
        else: 
            comp_turn_score = comp_turn_score + roll
    elif comp_choice == 2:
        print("Computer banked.")
        comp_total = comp_total + comp_turn_score
        comp_turn_score = 0
        comp_turns = comp_turns + 1

    if comp_turn_score >= 15:
        print("Computer banked.")
        comp_total = comp_total + comp_turn_score
        comp_turn_score = 0
        comp_turns = comp_turns + 1
    
    if comp_total >= 20:
        print(color.BOLD + "Computer wins! Computer score: " + str(comp_total))
        break
    if total >= 20:
        print(color.BOLD + "You win! Your score is: " + str(total))
        break
