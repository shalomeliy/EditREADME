```markdown
# World of Games: The Epic Journey

**Author: Shalom Eliyahu**  
**Title: DEVOPS**
\
## Overview
World of Games: The Epic Journey is a Python-based project that offers a variety of fun and engaging games. The project is designed to help users learn Python through interactive gameplay. The games included are a Memory Game, Guess Game, and Currency Roulette. This project is useful for anyone looking to practice Python programming, especially in a game development context.

## Project Requirements
- Python 3.x
- Flask (for serving scores)
- Requests (for Currency Roulette Game API)

## Installation
To get started with the World of Games, follow the installation instructions provided in the ~[installation docs](docs/installation.md)~  

## Level 1: Getting Started
Welcome to the World of Games: The Epic Journey! This guide will walk you through the initial steps to set up and run your Python program. Please follow the instructions below to start your coding adventure.

### Create a New Python Program: wog
Begin by creating a new Python program named wog. This program will serve as the foundation for your World of Games project.
\
### Develop Functions in `app.py`
In your `app.py` file, you will define two functions: `welcome()` and `start_play()`.

#### `welcome()`
This function takes a person's name as input and displays a personalized welcome message in the following format:

```
Hi [username] and welcome to the World of Games: The Epic Journey
```

#### `start_play()`
This function presents a list of available games to the user:

```
Please choose a game to play:
1. Memory Game - a sequence of numbers will appear for 1 second and you have to guess it back.
2. Guess Game - guess a number and see if you chose like the computer.
3. Currency Roulette - try and guess the value of a random amount of USD in ILS
```
\
The user will select a game by entering the corresponding number. After choosing a game, the function will prompt the user to select a difficulty level between 1 and 5.

### Implement the Main Execution in `main.py`
Create a new Python file named `main.py` to orchestrate the execution of your program. Your `main.py` file should include the following lines:
```python
welcome()
start_play()
```
This code imports the necessary functions from `app.py`, welcomes the user by name, and prompts the user to select a game and difficulty level.

### Submission Details
Prepare a compressed zip file containing the following files:
- `main.py`
- `app.py`

Ensure the files are organized and structured appropriately within the zip archive.

Congratulations! You've completed the first level of World of Games. Take pride in your progress and get ready to delve deeper into the exciting world of coding and game development. Remember to reach out if you encounter any challenges or need further assistance. Best of luck on your World of Games journey!
\
\
\
\
\
## Level 2: Game Modules

### Guess Game – `guess_game.py`
![Guess Game](https://t4.ftcdn.net/jpg/05/28/90/61/360_F_528906125_hIJGjopyvcymzICiHiwL1ne4kuMezhQn.jpg)

The Guess Game module is designed to initiate a new game by generating a random number within a specified range of 0 to a variable named difficulty. The game involves receiving a number input from the player based on the provided properties.

#### Functions
- **`generate_number`**: Generates a random number between 0 and the specified difficulty, saving it as the secret_number.
- **`get_guess_from_user`**: Prompts the user to input a number within the range of 0 to the difficulty and returns the entered number.
- **`compare_results`**: Compares the generated secret number with the user's input and determines if they match.
- **`play`**: Initiates the game by calling the functions above and returns True if the user wins, and False if the user loses.
\
\
\
\
\
### Memory Game – `memory_game.py`
The Memory Game module challenges players to remember a sequence of numbers that appear briefly on the screen and then input them correctly.
![Memory Game](https://i.ytimg.com/vi/vfnyXiKZftc/maxresdefault.jpg)
\
\
\
\
\
### Currency Roulette Game – `currency_roulette_game.py`
![Currency Roulette Game](https://media.tenor.com/eFt5IXNkP-UAAAAM/you-think-i-dont-know-math-math.gif)

The Currency Roulette Game module utilizes a free currency API to retrieve the current exchange rate from USD to ILS (Israeli Shekel). Players are tasked with guessing the value of a newly generated random number (between 1 to 100) in USD converted to ILS. The accuracy of their guess depends on the game's difficulty level.

#### Functions
- **`get_money_interval`**: Retrieves the current USD to ILS exchange rate and calculates an interval for the correct answer based on the game's difficulty level.
\
\
\
\
\
## Level 3: Score Modules

### Utils file – `utils.py`
A general-purpose Python file. This file will contain general information and operations we need for our games.

#### Variables
- **`SCORES_FILE_NAME`**: A string representing a file name. By default “Scores.txt”
- **`BAD_RETURN_CODE`**: A number representing a bad return code for a function.

#### Functions
- **`screen_cleaner`**: A function to clear the screen (useful when playing memory game or before a new game starts).

### Score utils file – `score.py`
A package that is in charge of managing the scores file. The scores file at this point will consist of only a number. That number is the accumulation of the winnings of the user. The amount of points for winning a game is as follows: POINTS_OF_WINNING = (DIFFICULTY X 3) + 5. Each time the user wins a game, the points they win will be added to their current amount of points saved in a file.

#### Functions
- **`add_score`**: The function’s input is a variable called difficulty. The function will try to read the current score in the scores file, if it fails it will create a new one and will use it to save the current score.

### Main scores file – `main_score.py`
This file’s sole purpose is to serve the user’s score currently in the `Scores.txt` file over HTTP with HTML. This will be done by using Python’s Flask library.

#### Functions
- **`score_server`**: This function will serve the score. It will read the score from the scores file and will return an HTML page displaying the score. If the function has a problem showing the result or reading the score, it will return an error page with a bad return code.
```
score_server():
    if request.get(app) == 200:
        url = f"""<html>
                    <head>
                        <title>Scores game</title>
                    </head>
                    <body>
                        <h1>The score is:</h1>
                        <div id="score" style="color:green">{utils.scores_file_name}</div>
                    </body>
                  </html>"""
    else:
        url = f"""
                <html>
                    <head>
                        <title>Scores Game</title>
                    </head>
                    <body>
                    <h1>ERROR:</h1>
                    <div id="score" style="color:red">{str(utils.bad_return_code)}</div>
                    </body>
                </html>"""
```
Function Update:
Change the function `start_play()` as follows: In case the user wins the game, the function will call `add_score` to add the new score the user won to the score saved in the `Scores.txt` file.

## Submission Details
These game modules have been meticulously designed to provide an engaging and challenging experience. Feel free to explore and enjoy the diverse gameplay offered by the World of Games!
```


