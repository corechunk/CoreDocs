# 41 | Tic-Tac-Toe Win Condition

Check if a Tic-Tac-Toe board has a winner.

---

## 1. The Objective
Return the character ('X' or 'O') that has three in a row.

---

## 2. Visual Logic
Check 8 possible lines:
- 3 Rows
- 3 Columns
- 2 Diagonals

---

## 3. The "Aha!" Moment
You don't need a search algorithm; just check the 8 specific winning patterns explicitly.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

char checkWinner(char b[3][3]) {
    // Rows and Cols
    for(int i=0; i<3; i++) {
        if(b[i][0] != ' ' && b[i][0] == b[i][1] && b[i][1] == b[i][2]) return b[i][0];
        if(b[0][i] != ' ' && b[0][i] == b[1][i] && b[1][i] == b[2][i]) return b[0][i];
    }
    // Diagonals
    if(b[0][0] != ' ' && b[0][0] == b[1][1] && b[1][1] == b[2][2]) return b[0][0];
    if(b[0][2] != ' ' && b[0][2] == b[1][1] && b[1][1] == b[2][0]) return b[0][2];
    
    return ' '; // No winner
}

int main() {
    char board[3][3] = {{'X','X','X'}, {'O',' ',' '}, {' ','O',' '}};
    std::cout << "Winner: " << checkWinner(board) << std::endl;
    return 0;
}
```
