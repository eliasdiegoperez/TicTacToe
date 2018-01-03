//
//  main.cpp
//  TicTacToe
//
//  Created by Elias Perez on 12/29/17.
//  Copyright © 2017 Elias Perez. All rights reserved.
//

#include <iostream>
#include <iomanip>
#include <cstdlib>
#include <ctime>

using namespace std;

void showGrid(char[3][3]);
void initializeGrid(char[3][3]);
void makeMove(int, int, char[3][3], char&, bool&);
void computerMove(char[3][3], char&);
bool checkDraw(char[3][3]);
bool checkRows(char[3][3]);
bool checkColumns(char[3][3]);
bool checkDiagnol(char[3][3]);
bool checkWinner(char[3][3]);
void exampleGrid();

int main(int argc, const char * argv[]) {
    char grid[3][3] = {};
    int row, column;
    char player = 'X';
    char repeat;
    bool valid = true;
    srand(time(NULL));
    
    cout << "Tic Tac Toe " << endl;
    cout << "By: Elias Perez" << endl;
    cout << "---------------" << endl;
    cout << "\n** To select spot type row and column number seperated by a space, then press enter. ** \n" << endl;
    
    do {
        cout << "Would you like to be X's or O's (X/O)?: ";
        cin >> player;
        initializeGrid(grid);
        exampleGrid();
        do {
            cout << "Select a spot: ";
            cin >> row >> column;
            makeMove(row, column, grid, player, valid);
            if(!checkWinner(grid) && valid) {
                computerMove(grid, player);
            }
            showGrid(grid);
    
        }while(!checkWinner(grid) && !checkDraw(grid));
        
        if(checkWinner(grid))
            cout << "\nWinner is player " << player << "!" << endl;
        else
            cout << "\nIt is a draw!" << endl;
        
        cout << "Do you want to play again (Y/N)?: ";
        cin >> repeat;
        
    }while(repeat != 'N');
    
    cout << "Game Over." << endl;
    
    return 0;
}

void exampleGrid() {
    cout << "0,0" << " | " << "0,1"<< " | " << "0,2" << endl;
    cout << "1,0" << " | " << "1,1" << " | " << "1,2" << endl;
    cout << "2,0" << " | " << "2,1" << " | " << "2,2" << endl;
}
void showGrid(char grid[3][3]) {
    cout << left << setw(3) << grid[0][0] << "| " << grid[0][1] << " | " << grid[0][2] << endl;
    cout << left << setw(3) << grid[1][0] << "| " << grid[1][1] << " | " << grid[1][2] << endl;
    cout << left << setw(3) << grid[2][0] << "| " << grid[2][1] << " | " << grid[2][2] << endl;
}

void initializeGrid(char grid[3][3]) {
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            grid[i][j] = '*';
        }
    }
}

void makeMove(int row, int column, char grid[3][3], char &player, bool &valid) {
    
    if (grid[row][column] != 'X' && grid[row][column] != 'O') {
        grid[row][column] = player;
        valid = true;
        if(checkWinner(grid)) {
            player = player;
        }
        else if (player == 'X') {
            player = 'O';
        }
        else
            player = 'X';
    }
    else {
        cout << "Move already made, select new position" << endl;
        valid = false;
    }
   
}

void computerMove(char grid[3][3], char &player) {
    if (!checkDraw(grid)) {
        int row = rand() % 3;
        int column = rand() % 3;
        while (grid[row][column] == 'X' || grid[row][column] == 'O') {
            row = rand() % 3;
            column = rand() % 3;
        }
        grid[row][column] = player;
        if(checkWinner(grid)) {
            player = player;
        }
        else if (player == 'X') {
            player = 'O';
        }
        else
            player = 'X';
    }
}

bool checkDraw(char grid[3][3]) {
    
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            if(grid[i][j] == '*') {
                return false;
            }
        }
    }
    return true;
}

bool checkRows(char grid[3][3]) {
    for (int i = 0; i < 3; i++) {
        if (grid[i][0] == grid[i][1] && grid[i][0] == grid[i][2] && grid[i][0] != '*') {
            return true;
        }
    }
    
    return false;
}

bool checkColumns(char grid[3][3]) {
    for (int j = 0; j < 3; j++) {
        if (grid[0][j] == grid[1][j] && grid[0][j] == grid[2][j] && grid[0][j] != '*') {
            return true;
        }
    }
    
    return false;
}

bool checkDiagnol(char grid[3][3]) {
   if(grid[0][0] == grid[1][1] && grid[0][0] == grid[2][2] && grid[0][0] != '*')
       return true;
    else if (grid[0][2] == grid[1][1] && grid[0][2] == grid[2][0] && grid[0][2] != '*')
        return true;
    
    return false;
}

bool checkWinner(char grid[3][3]) {
    if (checkRows(grid))
        return true;
    else if (checkColumns(grid))
        return true;
    else if (checkDiagnol(grid))
        return true;
    else
        return false;
}
