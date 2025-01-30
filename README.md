# N-Queen-Problem--gfg
The n-queens puzzle is the problem of placing n queens on a (n × n) chessboard such that no two queens can attack each other. Note that two queens attack each other if they are placed on the same row, the same column, or the same diagonal.

Given an integer n, find all distinct solutions to the n-queens puzzle.
You can return your answer in any order but each solution should represent a distinct board configuration of the queen placements, where the solutions are represented as permutations of [1, 2, 3, ..., n]. In this representation, the number in the ith position denotes the row in which the queen is placed in the ith column.
For eg. below figure represents a chessboard [3 1 4 2].

Examples:

Input: n = 1
Output: [1]
Explaination: Only one queen can be placed in the single cell available.
Input: n = 4
Output: [[2 4 1 3 ] [3 1 4 2 ]]
Explaination: There are 2 possible solutions for n = 4.
Input: n = 2
Output: []
Explaination: There are no possible solutions for n = 2.
 # code
 class Solution {
public:
    vector<vector<int>> nQueen(int n) {
        vector<vector<int>> result;
        vector<int> board(n, 0);
        solve(0, n, board, result);
        return result;
    }

private:
    void solve(int col, int n, vector<int>& board, vector<vector<int>>& result) {
        if (col == n) {
            result.push_back(board);
            return;
        }
        for (int row = 0; row < n; row++) {
            if (isSafe(board, col, row)) {
                board[col] = row + 1;
                solve(col + 1, n, board, result);
            }
        }
    }
    
    bool isSafe(vector<int>& board, int col, int row) {
        for (int i = 0; i < col; i++)
            if (board[i] - 1 == row || abs(board[i] - 1 - row) == abs(i - col))
                return false;
        return true;
    }
};
 
 
