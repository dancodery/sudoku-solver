# Artificial Intelligence Sudoku Solver

## Installation
1. Go to your directory.
2. `git clone https://github.com/dancodery/sudoku-solver.git`
3. `cd sudoku-solver`
4. Download and set up https://www.anaconda.com/download/
5. `conda info` to verify you installation was successful
6. Create a conda environment from the file `conda env create -f aind-environment-macos.yml`
7. Activate this environment `source activate aind`
8. Start `python sudoku-solver.py`
9. ? Download and install http://www.pygame.org/download.shtml if the graphical user interface is not starting on its own.

<img src='images/screenshot.png'>

## Usage

* `python sudoku-solver.py` will load the sudoku solver with an easy sudoku from the samples
* `python sudoku-solver.py '4.....8.5.3..........7......2.....6.....8.4......1.......6.3.7.5..2.....1.4......'` is your way of filling in your own sudoku which will be solved. It requires 81 characters inside of single quotation marks.
* `python sudoku-solver.py --diag '2.............62....1....7...6..8...3...9...7...6..4...4....8....52.............3'` is solving your feeded in sudoku. But it will also check the diagonal lines inside of the given sudoku. So from left-top to right-bottom and from left-bottom to right-top.
* `python sudoku-solver.py -h` is showing the help

## Documentation

The program is based on the Udacity.com Nanodegree Program 'Artificial Intelligence'.

In the highest level of solving the sudoku it uses **depth-first search and propagation** to try all possible values. 
But it is not just brute forcing all possible values. It begins to be more sophisticated in the lower levels. In the lower levels the program uses constraint propagation techniques to solve cells inside the sudoku.
So on the highest level, Depth-first search means that the program tries out and is coming back from guesses made by the program.
It is trial and error.
Imagine you have a sudoku and it is not solved yet. You can't make any progress anymore, because the underlaying techniques (eliminate, naked twins, only choice) make no progress anymore. But you have one certain cell with two possible digits. It makes sense to try out one of these two digits to see what impact it has on further predictions and if the sudoku can finally be solved. Thus if you can't go further anymore because it contradicts itself on further steps, you know that in this first cell there must be the second digit filled in.

The underlaying level **'constraint propagation'** is executed until it makes no progress anymore. It consists of 1. Eliminate, 2. Naked Twins and 3. Only Choice.

<img src='images/sudoku.png'>

A sudoku consists of 9 rows and 9 columns. We label the rows from A-I and the columns from 1-9.
The cell D5 means the cell in the fifth column and the fourth row.

A **unit** is one block of 9 digits which must contain each digit from 1-9 once. 
A sudoku has 9 row units. The first one is A1, A2, A3, A4, A5, A6, A7, A8, A9.

9 col units. The first one is A1, B1, C1, D1, E1, F1, G1, H1, I1.

9 square units. The first one is A1, A2, A3, B1, B2, B3, C1, C2, C3.

And optional 2 diagonal units.

### Eliminate


The elimination function looks for single digits in a cell which are contained in its peers as a possibility.
Peers are neighbors in any unit.

So if you have one row and in that row there is a cell with a single digit, you know that this digit can be deleted from the possibility list of all other cells.

### Naked Twins

This function searches for two of the same digits in two cells in one unit. If this sounds too complicated look at the picture below.
From this we conclude that these digits can be deleted from the possibilities in the other cells.

<img src='images/naked_twins.png'>

### Only Choice

This looks for digits in the probability list of a cell which occur once within a unit. So if you have one column and you take a look at the possibility lists of the cells in that column. Let's say, you discover that the digit '1' just occurs in the C row. So you can solve this cell and take this number as the only possibility.



The udacity course is based on http://norvig.com/sudoku.html

Please give me a star if you like this repo ;=)

Copyright 2017 **© Daniel Gockel**