# File I/O and Structs

## Learning goal

Working with own data types and data operation will be practiced using the hangman game.

## Description

Write a program, which reads word lists from a file. These word list is the base for multiple rounds hangman. In each round guess the user one letter at a time and has to find the guessing word in a limit of 11 turns.

## Data structure

Save the world list and the game result of the user(number of turns) in a simple linked list. The words should be save dynamic on the heap.

## File format

Word list should be saved as text data, where each word has its own line.

Single lines are terminated with a line break(\n). There are multiple spaces at the start and at the end of the line, but not between the words. Words may only consists of characters from english alphabet (A-Z and a-z).

If line does not meet the requirements, the vocabulary files is invalid (see error massages)

## Functionality

The program will be used via command line. There will provide the filename for the word list. May the program not find the file or the called
program doesn't require the requirements, it returns an error messages.

In each turn the program prints the opening word and the number of `'_'` (length of the guessing word) followed by `'([guess])'`(guess = number of wrong guessing of current word).

In another line, the user is promoted to enter a letter with the text `'Your guess: '`.

The program reads the letter of the user. Input is case insensitive. May the letter be in the guessing word, so all matching letter will be displayed, if not the [guess] counter will be raised by one.

If the value of [guess] is greater then 11, the player has lost. The guessing word will be displayed followed by `'(x_x)'`.

If the player guessed all words, he has won the round. The guessing word will be displayed followed by `'([guess])'`.

One round is played for each word in the list, in the order in which they appear in the imported file.

After the last round the text `'won ([correct]/[numtotal])'` displayed. `correct` = number of correct guessed words. `numtotal` = overall number of guessing words.

### Example

valid word list

```
Hangman
      Rs
```

invalid word list

```
Hangman Rs
```

Program call with valid word list and user input

```
$ cargo run hangman word_list.txt
H______ (0)
Your guess: A
Ha___a_ (0)
Your guess: n
Han__a_ (0)
Your guess: g
Hang_a_ (0)
Your guess: q
Hang_a_ (1)
Your guess: u
Hang_a_ (2)
Your guess: m
Hangma_ (2)
Your guess: n
Hangman (2)
R_ (0)
Your guess: t
R_ (1)
Your guess: h
R_ (2)
Your guess: b
R_ (3)
Your guess: t
R_ (4)
Your guess: z
R_ (5)
Your guess: u
R_ (6)
Your guess: i
R_ (7)
Your guess: o
R_ (8)
Your guess: a
R_ (9)
Your guess: z
R_ (9)
Your guess: d
R_ (10)
Your guess: f
Rs (x_x)
won (1/2)
```
To note: The '$' is the begin of the command line of the terminal.

### Return values

| value | description   | error messages              |
| :--:  | -----------   | -----------                 |
| 0     | Success | |
| 1     | wrong number of parameters                  | usage: cargo file [executable] filename\n |
| 2     | word file cannot be opend                   | ERROR: cannot open file [filename]\n |
| 3     | world list invalid                          | ERROR: file [filename] invalid\n |
| 4     | no more memory can be used                  | ERROR: Out of Memory\n |

## Specification

* No extra output
* All output take place at stdout
  * No output at stderr
* Data content has to be stored on the heap
  * World lists and game score are stored in linked lists on the heap
  * Word are stored as dynamic letters on the heap
