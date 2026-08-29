# Solution Valid Sudoku
## Approach:
- Step 1: The core idea is to use 2D arrays to keep track of the numbers on the Sudoku board.
- Step 2: Here, I create three boolean 2D arrays( intialized to false by default) based on the problem's
- rules: one for the rows, one for the columns, and one for the 3x3 sub-boxes.
- Step 3: the numbers themselves will treated as the indicies of these arrays to make marking them easier.
- Step 4: The final issue is handling the 3x3 sub-boxes. I use the formula (row / 3) * 3 + (column / 3) because
- it allows us to map or flatten a 3x3 block into linear array index.
## Complexity:
- Time complexity: O(n) because we traverse the array only once.
- Space complexity: O(1) because The Sudoku board has a fixed size of 9x9. The three arrays always use a constant amount of memory
  (exactly 243 booleans), independent of the input.

  ![Image boxes](docs/images/docs/images/Screenshot%202026-08-29%20230141.png)
```cpp
class Solution {
public:
    bool isValidSudoku(vector<vector<char>>& board) {
        int rows[9][9] = {false};
        int cols[9][9] = {false};
        int boxes[9][9] = {false};
        for(int i = 0; i < 9; i++){
            for(int j = 0; j < 9; j++){
                if(board[i][j] == '.'){
                    continue;
                }
                int index = board[i][j] - '1';
                int index_boxes = (i/3) * 3 + (j/3);
                if(rows[i][index] || cols[j][index] || boxes[index_boxes][index]){
                    return false;
                }
                rows[i][index] = true;
                cols[j][index] = true;
                boxes[index_boxes][index] = true;
            }
        }
        return true;
    }
};
```
## End
---
