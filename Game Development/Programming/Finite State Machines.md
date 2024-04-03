# Overview
A finite state machine consists of a fixed number of states. When a symbol, a character from some alphabet say, is input to the machine it changes state in such a way that the next state depends only on the current state and the input symbol.

Many programming problems are most easily solved by actually implementing a finite state machine. You set up an array, or other data structure, which stores the possible states and you implement a pointer to the location that is the current state. Each state contains a lookup table that shows what the next state is, given an input symbol. When a symbol is read in, your program simply has to look it up in the table and move the pointer to the new state. This a very common approach to organizing games.

# Abstract Example of a FSM

![[Pasted image 20240225160647.png]]
Given the above image, we begin at state 1. To create a FSM from states 1, 2, and 3, we will need actions A and B.
- State 1:
	- If A, move to state 2
	- If B, move to state 3
- State 2:
	- Per above diagram, once in State 2 you cannot leave state 2
- State 3:
	- If A, move to state 1.
# Tl;dr
A state machine consists of a collection of states an object can exist in, and creates a way to navigate through the states given an input.