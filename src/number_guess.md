This is a game in which users try to guess a random integer.

Rules:

An integer is selected randomly from a to b, inclusive. Players make guesses. When a player guesses correctly, the number is reset.

Initialization: the name of the game type is "number guess". The parameters are the integers a and b which are the least and greatest values, respectively, that the random integer could have. These are given as base ten integers separated by newlines.

Example: to create a game where users guess a number from 1 to 10, send the message 'nGame Name\nnumber guess\n1\n10'.

Communication: users send the server there guess as a base-10 string. The server replies with either 'Incorrect' or 'Correct'.