
# CODSOFT Project 1

This is a code for making Tic-Tak Toe game using C++ language

---
```C++
#include<bits/stdc++.h>
using namespace std;

class boardgame {
private:
    char board[3][3] = {{'1', '2', '3'}, {'4', '5', '6'}, {'7', '8', '9'}};
    int choice;
    int row;
    int column;
    char turn;
    bool draw;

public:
    boardgame() {
        choice = -1;
        row = -1;
        column = -1;
        turn = 'X';
        draw = false;
    }

    char getTurn() {
        return turn;
    }

    bool isDraw() {
        return draw;
    }

    void boardinterface() {
        cout << "          PLAYER - 1 [X]    PLAYER - 2 [O]" << endl;
        cout << endl;
        cout << "     |     |     " << endl;
        cout << "  " << board[0][0] << "  |  " << board[0][1] << "  |  " << board[0][2] << "  " << endl;
        cout << "_____|_____|_____" << endl;
        cout << "     |     |     " << endl;
        cout << "  " << board[1][0] << "  |  " << board[1][1] << "  |  " << board[1][2] << "  " << endl;
        cout << "_____|_____|_____" << endl;
        cout << "     |     |     " << endl;
        cout << "  " << board[2][0] << "  |  " << board[2][1] << "  |  " << board[2][2] << "  " << endl;
        cout << "     |     |     " << endl;
    }

 int getValidChoice() {
    int input;
    while (!(cin >> input) || input < 1 || input > 9) {
        cout << "Invalid choice. Please enter a valid position (1-9): ";
        cin.clear();
        cin.ignore(numeric_limits<streamsize>::max(), '\n');
    }
    return input;
}
void playerchances() {
    if (turn == 'X') {
        cout << "Player - 1 [X] turn: ";
    } else if (turn == 'O') {
        cout << "Player - 2 [O] turn: ";
    }
    choice = getValidChoice();

    switch(choice){
        case 1: row=0; column=0; break;
        case 2: row=0; column=1; break;
        case 3: row=0; column=2; break;
        case 4: row=1; column=0; break;
        case 5: row=1; column=1; break;
        case 6: row=1; column=2; break;
        case 7: row=2; column=0; break;
        case 8: row=2; column=1; break;
        case 9: row=2; column=2; break;
    }

    if(turn == 'X' && board[row][column] != 'X' && board[row][column] != 'O'){
        //for PLAYER 1 .. filling the choice made,if loaction is not filled
        board[row][column] = 'X';
        turn = 'O';
    }else if(turn == 'O' && board[row][column] != 'X' && board[row][column] != 'O'){
        //for PLAYER 2 .. filling the choice made,if loaction is not filled
        board[row][column] = 'O';
        turn = 'X';
    }else {
        cout<<"Position is occupied ! Choose different Position"<<endl;
        playerchances();
    }
}

           
    bool gameconclusion() {
        for (int i = 0; i < 3; i++) {
            if ((board[i][0] == board[i][1] && board[i][0] == board[i][2]) || (board[0][i] == board[1][i] && board[0][i] == board[2][i])) {
                return false;
            }
        }

        if ((board[0][0] == board[1][1] && board[0][0] == board[2][2]) || (board[0][2] == board[1][1] && board[0][2] == board[2][0])) {
            return false;
        }

        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 3; j++) {
                if (board[i][j] != 'X' && board[i][j] != 'O') {
                    return true;
                }
            }
        }

        draw = true;
        return false;
    }
};
void starting(boardgame &bl);

void playgame() {
    boardgame bl;
    starting(bl);
}

void starting(boardgame &bl) {
    while (bl.gameconclusion()) {
        bl.boardinterface();
        bl.playerchances();
    }

    if (bl.getTurn() == 'X' && !bl.isDraw()) {
        cout << "Congratulations! Player - 2 "<< endl;
    } else if (bl.getTurn() == 'O' && !bl.isDraw()) {
        cout << "Congratulations! Player - 1 " << endl;
    }else{
        cout<<"Game Draw !"<<endl;
    }

    cout << endl;
    cout << "Play again? Y or N" << endl;
    char ch;
    cin >> ch;
    if (ch == 'Y') {
        // Clear the board and restart the game
        playgame();
    } else {
        cout << "Thank You!" << endl;
        return;
    }
}

int main() {

    playgame();
    


    return 0;
}
```
---


## Authors

- [@chitrangv27](https://github.com/chitrangv27)

