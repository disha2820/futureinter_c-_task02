# futureinter_c-_task02
#include <iostream>
#include <cstdlib> // For rand() and srand()
#include <ctime>   // For time()
using namespace std;

string getComputerChoice() {
    int choice = rand() % 3; // Generate 0, 1, or 2
    if (choice == 0)
        return "Rock";
    else if (choice == 1)
        return "Paper";
    else
        return "Scissors";
}

string determineWinner(string userChoice, string computerChoice) {
    if (userChoice == computerChoice)
        return "It's a tie!";
    else if ((userChoice == "Rock" && computerChoice == "Scissors") ||
             (userChoice == "Paper" && computerChoice == "Rock") ||
             (userChoice == "Scissors" && computerChoice == "Paper"))
        return "You win!";
    else
        return "Computer wins!";
}

int main() {
    srand(time(0)); // Seed the random number generator
    string userChoice, computerChoice, playAgain;

    cout << "Welcome to Rock-Paper-Scissors!" << endl;

    do {
        // User input
        cout << "Enter your choice (Rock, Paper, Scissors): ";
        cin >> userChoice;

        // Validate input
        if (userChoice != "Rock" && userChoice != "Paper" && userChoice != "Scissors") {
            cout << "Invalid choice. Please enter Rock, Paper, or Scissors." << endl;
            continue;
        }

        // Computer choice
        computerChoice = getComputerChoice();
        cout << "Computer chose: " << computerChoice << endl;

        // Determine and display winner
        cout << determineWinner(userChoice, computerChoice) << endl;

        // Ask if the user wants to play again
        cout << "Do you want to play again? (yes/no): ";
        cin >> playAgain;

    } while (playAgain == "yes");

    cout << "Thank you for playing!" << endl;

    return 0;
}
