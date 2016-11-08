# 04_Lab

Main lab #4 - Plinko
Background

Your best friend bought tickets for the both of you to go to The Price Is Right this weekend. On the extremely small chance that your name gets called, you want to be ready to win as much money as possible. Instead of preparing for a wide variety of games, though, you put all of your effort into the one game that truly matters: Plinko.

To practice your Plinko skills, you've decided to write a C++ program to simulate a game of Plinko and to compute average winnings based on where you drop your chips.
Requirements

If you are not familiar with Plinko, you may want to play it a bit before beginning the lab. An online version of Plinko can be found at http://www.kongregate.com/games/StapleGun/plinko. Note that the dimensions, prizes, or other details may be different in the demo from the requirements of this lab. Use the values specified here, not those found in the demo. You can also find a picture of a Plinko board in "Content" in Learning Suite under the title "Plinko Picture". We assume the Plinko board looks exactly like the one shown in Learning Suite. Go to the Style Guide at the end of test cases section to see instruction relating to Plinko test cases.
Part 1 - The Menu (19 points)

Prompt the user to select one of three operations (your program must use the options 0, 1, and 2):

    0 - Quit the program
    1 - Drop a single chip into one slot
    2 - Drop multiple chips into one slot

After any operation is complete (except for quitting), return the user to your menu and reprompt the user to select another operation. For Part 1, only the quit operation needs to work.

If an incorrect option is entered, you must re-prompt the user to select another operation, that is, return the user to the menu.
Part 2 - Let the Chips Fall (24 points)

    Allow the user to drop one chip into one slot
    Prompt the user to select a slot into which he or she will drop a chip
    If the specified slot is not in the range 0 to 8, immediately return the user to the menu
    During simulation, report the path of the chip as it falls
    Report the amount of money won for the chip

Part 3 - Bowl of Chips (32 points)

    Allow the user to drop any number of chips into one slot
    Prompt the user to enter the number of chips to drop
    If the number of chips is non-positive (including 0), immediately return the user to the menu
    Prompt the user to select one slot into which he or she will drop the chips
    If the specified slot is not in the range 0 to 8, immediately return the user to the menu
    Report the total and average amount of money won for all chips rounded to the nearest penny
    Do NOT report the path of each chip as it falls down the plinko board for the "Bowl of Chips" part.

Implementation

    To ensure that your random path matches the auto-grader you MUST:
        Upon encountering a peg, a chip has a 50/50 chance of going left or right. Use "rand() % 2" to get a random value. If you get 0 decrease the chip position value, and if you get 1 increase the position value.
        Call rand() EXACTLY once at each step down through the pegs, even if you are on an edge and thus your decision will be forced. Specifically, after drawing the random number and determining which direction the chip is to fall, assure that this movement will not take the chip off of the board. If the movement would take the chip off of the board then move the chip in the opposite direction instead (chip locations must never be less than 0 and must never be greater than 8).
        You must set the random seed in the main function. Normally we would use "srand(time(0))" to get (more nearly) random behavior. However, in this lab you must use srand(42) at the start of main. Note also that you may get different behavior on different computers, so if you are running this lab somewhere other than on zybooks, you may not get the output shown above.
    If the user gives invalid input, do not re-prompt for a good input; invalid input under any option should merely return the user to the menu. You may assume that the input will be an integer in all cases. Your output should state that the input is invalid (as shown in the example) before displaying the menu again.

Plinko Board Notes

    A Plinko board consists of 9 input slots and 9 output slots. We will refer to these slots in c++ style, so they are named "slot 0" - "slot 8". The money won for a chip is determined by the slot the chip falls into at the end as indicated here and as shown on the image in learning suite:
        slot 0 yields $100.0
        slot 1 yields $500.0
        slot 2 yields $1000.0
        slot 3 yields nothing ($0.00)
        slot 4 yields $10000.0
        slot 5 yields nothing ($0.00)
        slot 6 yields $1000.0
        slot 7 yields $500.0
        slot 8 yields $100.0

    Between the input and output slots, there are 12 rows of pegs, with each row's pegs centered directly under the spaces from the row of pegs above as shown in the image found in learning suite.

    The Learning Suite image demonstrates the board, its slot numbers, its prizes, and two sample paths.
        The left path displays the position of the chip at each step; the right path shows red pegs whenever the left (or right) decision is forced.
        For the left path in the example, the following is the expected location report: [3.0 3.5 3.0 2.5 3.0 2.5 2.0 2.5 3.0 3.5 4.0 3.5 4.0]

Items Graded by the TA's Inspection (25 points)

    Adherence to the Style guidelines.
    You must also use loops at every appropriate opportunity (maximum 10 points deduction).
    You will not receive any credit if you use the c++ command "goto".

Notes

The test cases start with just the input part, so you can start there and then build your solution step by part. Also, you can submit your code as many times as you like.
Sample

Since we are now running in Visual Studio, we can see the input and output in a single stream. The test cases are still written in terms of separate input and output, but this sample shows the operation as the program would appear running in Visual Studio.

Welcome to the plinko simulator!

MENU: Please select one of the following options:

0 - Quit the program
1 - Drop a single chip into one slot
2 - Drop multiple chips into one slot

Enter your selection now: -1

INVALID SELECTION.  Please enter 0, 1 or 2

MENU: Please select one of the following options:

0 - Quit the program
1 - Drop a single chip into one slot
2 - Drop multiple chips into one slot

Enter your selection now: 3

INVALID SELECTION.  Please enter 0, 1 or 2

MENU: Please select one of the following options:

0 - Quit the program
1 - Drop a single chip into one slot
2 - Drop multiple chips into one slot

Enter your selection now: 1

*** DROP SINGLE CHIP ***

Which slot do you want to drop the chip in (0-8)? -1

INVALID SLOT.

MENU: Please select one of the following options:

0 - Quit the program
1 - Drop a single chip into one slot
2 - Drop multiple chips into one slot

Enter your selection now: 1

*** DROP SINGLE CHIP ***

Which slot do you want to drop the chip in (0-8)? 9

INVALID SLOT.

MENU: Please select one of the following options:

0 - Quit the program
1 - Drop a single chip into one slot
2 - Drop multiple chips into one slot

Enter your selection now: 1

*** DROP SINGLE CHIP ***

Which slot do you want to drop the chip in (0-8)? 5

*** DROPPING CHIP INTO SLOT 5 ***
PATH: [5.0 4.5 4.0 4.5 5.0 4.5 4.0 4.5 4.0 4.5 5.0 4.5 5.0]
WINNINGS: $0.00

MENU: Please select one of the following options:

0 - Quit the program
1 - Drop a single chip into one slot
2 - Drop multiple chips into one slot

Enter your selection now: 2

*** DROP MULTIPLE CHIPS ***

How many chips do you want to drop (>0)? -1

INVALID NUMBER OF CHIPS.

MENU: Please select one of the following options:

0 - Quit the program
1 - Drop a single chip into one slot
2 - Drop multiple chips into one slot

Enter your selection now: 2

*** DROP MULTIPLE CHIPS ***

How many chips do you want to drop (>0)? 142

Which slot do you want to drop the chip in (0-8)? 7

Total Winnings on 142 chips: 115100.00
Average winnings per chip: 810.56

MENU: Please select one of the following options:

0 - Quit the program
1 - Drop a single chip into one slot
2 - Drop multiple chips into one slot

Enter your selection now: 0

GOODBYE!
