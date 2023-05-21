# rock-paper-scissors

## What is the problem (aka understand)?
The problem is that I need to write a js program that allows the user to enter a case-insensitive string (either rock, paper, or scissors), which will then be compared against a randomly generated choice (either rock, paper, or scissors) for the computer. Based on those 2 choices, a winner or tie will be declared for the round (via the console), then this will repeat for a total of 5 rounds. After all five rounds, the player with the most wins will be declared the winner of the overall game, else it will be declared a tie.

Rock beats scissors, scissors beats paper, and paper beats rock. Any options vs itself results in a tie. 

## Plan

1. Does your program have a user interface? What will it look like? What functionality will the interface have? Sketch this out on paper.

    No, the program will not have a user interface at this point and will be played entirely within the console. 

2. What inputs will your program have? Will the user enter data or will you get input from somewhere else?

    Inputs will be a string (either rock, paper, or scissors) from the user (via a prompt() popup box) to declare their choice. This string can be uppercase, lowercase, or a mix of the two. Users will choose a string 5 times (once per each of the five rounds) until the game is over. 

    I don't think this is necessary at this point, but another potential input could be the user choosing whether or not they want to play another game (i.e., to reset the game and start over).

3. What’s the desired output?

    The desired output after a single round is a string that declares the winner of the round or a tie. 

    The desired output after all 5 rounds are complete is a string that declares who won or a tie based on the results of the 5 rounds that were played. 

4. Given your inputs, what are the steps necessary to return the desired output? Write a high level algorithm here. 

    The user is prompted to enter a choice
    The user inputs a choice 
    The computer will randomly generate a choice of its own 
    Those two choices will be compared
      If the user chose rock and the computer chose scissors, then the user wins 
      If the user chose rock and the computer chose paper, then the the user loses 
      If the user chose rock and the computer chose rock, then it's a tie
      If the user chose paper and the computer chose rock, then the user wins 
      If the user chose paper and the computer chose scissors, then the user loses
      If the user chose paper and the computer chose paper, then it's a tie
      If the user chose scissors and the computer chose paper, then the user wins
      If the user chose scissors and the computer chose rock, then the user loses
      If the user chose scissors and the computer chose scissors, then  it's a tie
    The result of the round will returned (aka stored)
    The returned result will then be displayed in the console
    This loops for a total of 5 rounds 
    Then after the 5th round the returned results from each round are compared 
      If the user won 3 rounds or more, then the console prints that the user is the winner
      If the computer won 3 rounds of more, then the console prints that the computer is the winner 
      Else the console prints the it was a tie overall
    Optional: the user is prompted on whether they want to play again
      If the user chose yes, then the game resets
      If the user chose no, the game stops there and nothing happens

## Game V1 (no loop)

      /*generate a random choice for the computer*/      
      function getComputerChoice() {
        let computerOptions = ["Rock", "Paper", "Scissors"];
        let computerChoice = computerOptions[Math.floor(Math.random() * computerOptions.length)];
        console.log("The computer chose: " + computerChoice);
        return computerChoice;
      }

      /*prompt the player to make a choice*/
      function playerSelectionPrompt() {
        let playerPrompt = prompt("Please choose Rock, Paper, or Scissors")
        selectionFirstLetter = playerPrompt.slice(0, 1);
        selectionRest = playerPrompt.slice(1);
        console.log("You chose: " + selectionFirstLetter.toUpperCase() + selectionRest.toLowerCase())
        return selectionFirstLetter.toUpperCase() + selectionRest.toLowerCase();
      }

      /*play a single round of rock paper scissors and return the result of the round*/
      function playRound(playerSelection, computerSelection) {
        if (playerSelection === "Rock" && computerSelection === "Scissors") {
          return "You win!";
        } else if (playerSelection === "Rock" && computerSelection === "Paper") {
          return "You lose";
        } else if (playerSelection === "Rock" && computerSelection === "Rock") {
          return "It's a tie!";
        } else if (playerSelection === "Paper" && computerSelection === "Rock") {
          return "You win!";
        } else if (playerSelection === "Paper" && computerSelection === "Scissors") {
          return "You lose";
        } else if (playerSelection === "Paper" && computerSelection === "Paper") {
          return "It's a tie!";
        } else if (playerSelection === "Scissors" && computerSelection === "Paper") {
          return "You win!";
        } else if (playerSelection === "Scissors" && computerSelection === "Rock") {
          return "You lose";
        } else if (playerSelection === "Scissors" && computerSelection === "Scissors") {
          return "It's a tie!";
        }
      }

      /*note, the test from step 5 doesn't work but console.log(playRound(playerSelectionPrompt(), getComputerChoice())); does work?*/

      /*playRound(playerSelectionPrompt(), getComputerChoice()); this will run the game, but not display the win/lose/tie result unless you wrap it in a console.log. However, if I run that without the console.log in the actual browser console, then it will show the win/lose/tie result. Not sure why there's a difference?*/

      /*play an entire 5 round game, then return the overall win/lose/tie result*/
      let result;
      
      function game() {
        result = playRound(playerSelectionPrompt(), getComputerChoice());
        console.log(result);
        keepScore();
        result = playRound(playerSelectionPrompt(), getComputerChoice());
        console.log(result);
        keepScore();
        result = playRound(playerSelectionPrompt(), getComputerChoice());
        console.log(result);
        keepScore();
        result = playRound(playerSelectionPrompt(), getComputerChoice());
        console.log(result);
        keepScore();
        result = playRound(playerSelectionPrompt(), getComputerChoice());
        console.log(result);
        keepScore();
        console.log(gameResult());
      }
      
      /*keep track of players' scores after each round*/
      let playerScore = 0;
      let computerScore = 0;
      
      function keepScore() {
        if (result === "You win!") {
          playerScore = playerScore +1;
        } else if (result === "You lose") {
          computerScore = computerScore +1;
        } else if (result === "It's a tie!") {
          playerScore = playerScore +1;
          computerScore = computerScore +1;
        }
      }

      /*calculate the results after all 5 rounds are finished*/
      function gameResult() {
        if (playerScore > computerScore) {
          return "Game result: you win!";
        } else if (computerScore > playerScore) {
          return "Game result: you lose.";
        } else if (playerScore === computerScore) {
          return "Game result: it's a tie!";
        }
      }

      game();
