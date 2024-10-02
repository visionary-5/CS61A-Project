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


## Project 2: The  Game of Cats

### Introduction
In this project, you will write a program that measures typing speed. Additionally, you will implement typing autocorrect, which is a feature that attempts to correct the spelling of a word after a user types it. This project is inspired by typeracer.

### Final product
Our staff solution to the project can be interacted with at cats.cs61a.org. If you'd like, feel free to try it out now. When you finish the project, you'll have implemented a significant part of this match yourself!
