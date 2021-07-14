#include <iostream>
#include <string> 
#include <cstdlib>  
#include <ctime>
using namespace std;
void rules(){system("cls");
    cout << "\t\t=<=>=<=>=SPN NUMBER GUESSING RULES!=<=>=<=>=\n";
    cout << "\t1. Choose a number between 1 to 10\n";
    cout << "\t2. Winner gets 5 times of the money bet\n";
    cout << "\t3.You have 3 chance, Wrong bet, and you lose the amount you bet\n\n";}
int main()
{
    string playerName;
    int balance;
    int betAmount;
    int guess;
    int dice;
    int damn=0;
    int spn=2;
    int i; 
    char choice;
    srand(time(0)); 
    cout << "\n\t\t========WELCOME TO SPN NUMBER GUESSING=======\n\n";
    cout << "\n\nWhat's your Name : ";
    getline(cin, playerName);
    cout << "\n\nEnter the starting balance to play game : $";
    cin >> balance;
    do
    {
        system("cls");
        rules();
        cout << "\n\nYour current balance is $ " << balance << "\n";

        do
        {
            cout << "Hey, " << playerName<<", enter amount to bet : $";
            cin >> betAmount;
            if(betAmount > balance)
                cout << "Betting balance can't be more than current balance!🙄\n"
                       <<"\nRe-enter balance\n ";
        }while(betAmount > balance);

        do
        {
            cout << "Guess any betting number between 1 & 10 :";
            cin >> guess;
            damn=0,spn=2;
            if(guess <= 0 || guess > 10)
                cout << "\nNumber should be between 1 to 10\n"
                    <<"Re-enter number:\n ";
        }while(guess <= 0 || guess > 10);
        dice = rand()%10 + 1;
        for(i=0;i<2;i++){if(dice==guess){damn=1;
 break;}
 cout<<"you have "<<spn<<" chance "<<"guess your no number again 😢"<<endl;
 cin>>guess;
 spn--;
        	}
        if(damn== 1)
        {
            cout <<" congratulations 🥳🥳🥳 You have won 😍 Rs." << betAmount * 5;
            balance = balance + betAmount * 5;
        }
        else
        {
            cout << "damn 😭 😭 😭 you lost yours $" <<betAmount<<" better luck next time !! " << "\n";
            balance = balance - betAmount;
        }
        cout << "\nThe winning number was : " << dice <<"\n";
        cout << "\n"<<playerName<<", You have balance of " << balance << "$\n";
        if(balance == 0)
        {
            cout << "You have no money to play 🥺 ";
            break;
        }
        cout << "\n\n-->Do you want to play again (y/n)? ";
        cin >> choice;
    }while(choice =='Y'|| choice=='y');
    cout << "\n\n\n";
    cout << "\n\nThanks for playing the game. Your balance is " << balance <<"$\n\n";
    return 0;
}

