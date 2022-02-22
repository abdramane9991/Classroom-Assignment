#include <stdio.h>
#include <time.h> // contains prototype for function time.

/* run this program using the console pauser or add your own getch, system("pause") or input loop */

// enumeration constants represent game status

enum Status { CONTINUE, WON, LOST};

int rollDice(void); // function prototype
int main(void)

{
 // randomize random number generator using current time
 Srand(time (NULL));

 int myPoint; // player must make this point to win
 enum Status gameStatus; // can contain CONTINUE, WON, or LOST
 int sum = rollDice(); // first roll of dice

  // determine game Status based on sum of dice

  switch(sum) {

  	// win on first roll
  	case 7: // 7 is a winner
  	case 11: // 11 is a winner
  	gameStatus = WON;
  	break;

  	// lost on first roll
  	case 2: // 2 is a loser
  	case 3: // 3 is a loser
  	case 12: // 12 is a loser
  	gameStatus = LOST;
  	break;

  	// remember Point
  	Default:
  		gameStatus = CONTINUE; // player should keep rolling

  		myPoint = sum; // remember the point
  		printf ("Point is %d\n ", myPoint);
  		break; // optional

  }

  // while game not complete
  while( CONTINUE == gameStatus) { // player should keep rolling
  	sum = rollDice(); // rollDice again

  	// determine gameStatus
  	if (sum == myPoint){ // win by making point
  	gameStatus = WON;
  		}
  		else {
		  if(7 == sum) { // lose by rolling 7
		  gameStatus = LOST;
		  }
		  }
	}
	// display won or lost message
	if(WON == gameStatus){ // did player win?
	Puts("Player wins");
	}
	else { // player lost
	Puts(" Player loses");
	}
}
 // roll dice, calculate sum and display results
 int rollDice(void)
 {
 	int die1 = 1+(rand()% 6); // pick random die1 value
 	int die2 = 1+(rand()% 6); // pick random die2 value

 	// display results of this roll
 	printf("Player rolled %d + %d = %d\n", die1, die2, die1 + die2);


	return die1 + die2; // return sum of dice
}
