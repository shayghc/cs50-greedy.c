# cs50-greedy.c
CS50 pset1 greddy.c exercise

This code is throwing up some issues with check50. The while loop that calculates the one cent coins required only executes intermittently. I see no problem with the code myself so would appreciate some feedback to identify the issue here.

##Code is below, includes are cs50.h and stdio.h:

include <cs50.h>
include <stdio.h>

float change;
int count = 0;

int main(void) {

    // User input of change owed with negative value repeat prompt
    do {
    printf("How much change is owed?\n");
    change = get_float();
    } while (change < 0);
    
    // find minimum number of coins to provide the correct change
    while (change >= 0.25) // Quarters
    {
        change -= 0.25;
        count++;
    }

    while (change >= 0.10) // 10 cent coins
    {
        change -= 0.1;
        count++;
    }

    while (change >= 0.05) // 5 cent coins
    {
        change -= 0.05;
        count++;
    }
    
    while (change >= 0.01) // 1 cent coins  // This is the loop causing the issue with check50
    {
        change-= 0.01;
        count++;
    }
    printf("%i\n", count);
}

## check50 results

~/workspace/pset1/ $ check50 2016.greedy greedy.c

:) greedy.c exists

:) greedy.c compiles

:( input of 0.41 yields output of 4
   \ expected output, but not "3\n"
   
:( input of 0.01 yields output of 1
   \ expected output, but not "0\n"
   
:) input of 0.15 yields output of 2

:) input of 1.6 yields output of 7

:) input of 23 yields output of 92

:( input of 4.2 yields output of 18
   \ expected output, but not "22\n"
   
:) rejects a negative input like -.1

:) rejects a non-numeric input of "foo"

:) rejects a non-numeric input of ""

https://sandbox.cs50.net/checks/8eee09fd7628430499c4e99bb63e61bc
               
