# CS61A-Project

## Project 1: The Game of Hog

### Introduction
In this project, you will develop a simulator and multiple strategies for the dice game Hog. You will need to use control statements and higher-order functions together, as described in Sections 1.2 through 1.6 of Composing Programs, the online textbook.

### Basic Rules
1. In Hog, two players alternate turns trying to be the first to end a turn with at least 100 total points. On each turn, the current player chooses some number of dice to roll, up to 10. That player's score for the turn is the sum of the dice outcomes. However, a player who rolls too many dice risks:

2. Sow Sad. If any of the dice outcomes is a 1, the current player's score for the turn is 1.

### Special Rules
In a normal game of Hog, those are all the rules. To spice up the game, we'll include some special rules:

1. Hefty Hogs. If the opponent's score is 0 and the player chooses to roll zero dice, the player will get 1 point. However, if the opponent's score is not 0, a player who chooses to roll zero dice will gain points according to the following:
The opponent's score will be mapped to a series of functions to be applied to the player's score, starting from the rightmost digit (the one's place) and ending on the leftmost digit.
Each digit from 0 to 9 corresponds to a pre-defined function, f0 through f9.
The result of this series of calls modulo 30 is the amount of points the player receives for the turn.

2. Hog Pile. After points for the turn are added to the current player's score, if the one's digit (ones_digit) of the current player's score is the same as the one's digit of the opponent player's score, the current player gains an additional ones_digit points.

### Final product
You can try out the online Hog GUI with the staff solution to the project at hog.cs61a.org. When you finish the project, you'll have implemented a significant part of this game yourself.


## Project 2: The Game of Cats

### Introduction
In this project, you will write a program that measures typing speed. Additionally, you will implement typing autocorrect, which is a feature that attempts to correct the spelling of a word after a user types it. This project is inspired by typeracer.

### Final product
Our staff solution to the project can be interacted with at cats.cs61a.org. If you'd like, feel free to try it out now. When you finish the project, you'll have implemented a significant part of this match yourself!


## Project 3: The Game of Ants

### Introduction
In this project, you will create a tower defense game called Ants Vs. SomeBees. As the ant queen, you populate your colony with the bravest ants you can muster. Your ants must protect their queen from the evil bees that invade your territory. Irritate the bees enough by throwing leaves at them, and they will be vanquished. Fail to pester the airborne intruders adequately, and your queen will succumb to the bees' wrath. This game is inspired by PopCap Games' Plants Vs. Zombies.

This project uses an object-oriented programming paradigm, focusing on material from Chapter 2.5 of Composing Programs. The project also involves understanding, extending, and testing a large program.


### The Game
A game of Ants Vs. SomeBees consists of a series of turns. In each turn, new bees may enter the ant colony. Then, new ants are placed to defend their colony. Finally, all insects (ants, then bees) take individual actions. Bees either try to move toward the end of the tunnel or sting ants in their way. Ants perform a different action depending on their type, such as collecting more food or throwing leaves at the bees. The game ends either when a bee reaches the end of the tunnel (you lose), the bees destroy the QueenAnt if it exists (you lose), or the entire bee fleet has been vanquished (you win).

### Core concepts
The Colony. This is where the game takes place. The colony consists of several Places that are chained together to form a tunnel where bees can travel through. The colony also has some quantity of food which can be expended in order to place an ant in a tunnel.

Places. A place links to another place to form a tunnel. The player can put a single ant into each place. However, there can be many bees in a single place.

The Hive. This is the place where bees originate. Bees exit the beehive to enter the ant colony.

Ants. Players place an ant into the colony by selecting from the available ant types at the top of the screen. Each type of ant takes a different action and requires a different amount of colony food to place. The two most basic ant types are the HarvesterAnt, which adds one food to the colony during each turn, and the ThrowerAnt, which throws a leaf at a bee each turn. You will be implementing many more!

Bees. In this game, bees are the antagonistic forces that the player must defend the ant colony from. Each turn, a bee either advances to the next place in the tunnel if no ant is in its way, or it stings the ant in its way. Bees win when at least one bee reaches the end of a tunnel.

### Core classes
The concepts described above each have a corresponding class that encapsulates the logic for that concept. Here is a summary of the main classes involved in this game:

GameState: Represents the colony and some state information about the game, including how much food is available, how much time has elapsed, where the AntHomeBase is, and all the Places in the game.
Place: Represents a single place that holds insects. At most one Ant can be in a single place, but there can be many Bees in a single place. Place objects have an exit to the left and an entrance to the right, which are also places. Bees travel through a tunnel by moving to a Place's exit.
Hive: Represents the place where Bees start out (on the right of the tunnel).
AntHomeBase: Represents the place Ants are defending (on the left of the tunnel). If Bees get here, they win :(
Insect: A superclass for Ant and Bee. All insects have health attribute, representing their remaining health, and a place attribute, representing the Place where they are currently located. Each turn, every active Insect in the game performs its action.
Ant: Represents ants. Each Ant subclass has special attributes or a special action that distinguish it from other Ant types. For example, a HarvesterAnt gets food for the colony and a ThrowerAnt attacks Bees. Each ant type also has a food_cost attribute that indicates how much it costs to deploy one unit of that type of ant.
Bee: Represents bees. Each turn, a bee either moves to the exit of its current Place if the Place is not blocked by an ant, or stings the ant occupying its same Place.
Game Layout

### Playing the game
The game can be run in two modes: as a text-based game or using a graphical user interface (GUI). The game logic is the same in either case, but the GUI enforces a turn time limit that makes playing the game more exciting. The text-based interface is provided for debugging and development.

The files are separated according to these two modes. ants.py knows nothing of graphics or turn time limits.

To start a text-based game, run

```python3 ants_text.py```
To start a graphical game, run

```python3 gui.py```
