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



## Divide 
Take the algorithm from Q4 above, and break it down into smaller sub-steps to solve sub-problems. Write more in-depth pseudocode here. 

  Round starts => playRound(playerSelection, computerSelection) 

  The user is prompted to enter a choice => playerPrompt (use onload="FUNCTIONNAMEGOESHERE!!!!()" in the body tag to have the prompt come up as soon as the page loads)
  The user inputs a choice => playerSelection
  The computer will randomly generate a choice of its own => getComputerChoice
  
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

## Extra code

/*play entire 5 round game*/
      let roundResult = playRound(playerSelectionPrompt(), getComputerChoice(computerOptions));

      function game() {
        for (let i = 0; i < 5; i++) {
          playRound(playerSelectionPrompt(), getComputerChoice(computerOptions));
          console.log(roundResult);
          /*scoreKeeper();*/
        }
        /*return console.log(gameResult());*/
      }
  
      /*keep track of and adjust the players' scores after each round*/
      let playerScore = 0;
      let computerScore = 0;

      function scoreKeeper() {
        if (roundResult === "You win!") {
          playerScore = playerScore + 1;
        } else if (roundResult === "You lose") {
          computerScore = computerScore + 1;
        } else if (roundResult === "It's a tie") {
          playerScore = playerScore + 1;
          computerScore = computerScore + 1;
        }
        console.log(playerScore, computerScore);
      }

      /*determines who won the overall game*/
      function gameResult() {
        if (playerScore > computerScore) {
          return "Game result: you won the game!";
        } else if (computerScore > playerScore) {
          return "Game result: you lost the game";
        } else if (playerScore == computerScore) {
          return "Game result: it's a tie game!";
        }
      }

      /*run game*/
      game();