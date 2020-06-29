#  Unique Paths
A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

How many possible unique paths are there?

![](https://assets.leetcode.com/uploads/2018/10/22/robot_maze.png)

Above is a 7 x 3 grid. How many possible unique paths are there?

## Example 1:
```
Input: m = 3, n = 2
Output: 3
Explanation:
From the top-left corner, there are a total of 3 ways to reach the bottom-right corner:
1. Right -> Right -> Down
2. Right -> Down -> Right
3. Down -> Right -> Right
```
## Example 2:
```
Input: m = 7, n = 3
Output: 28
 ```

## Constraints:
```
1 <= m, n <= 100
It's guaranteed that the answer will be less than or equal to 2 * 10 ^ 9.
```
## Code
```
class Solution {
   public int uniquePaths(int m, int n) {
    int[][] mem = new int[m][n];
 
    //init with -1 value
    for(int i=0; i<m; i++){
        for(int j=0; j<n; j++){
            mem[i][j]=-1;
        }
    }
 
    return helper(mem, m-1, n-1);
}
 
private int helper(int[][] mem, int m, int n){
    //edge has only one path
    if(m==0||n==0){
        mem[m][n]=1;
        return 1;
    }
 
    if(mem[m][n]!=-1){
        return mem[m][n];
    }
 
    mem[m][n] = helper(mem, m, n-1) + helper(mem, m-1, n);
 
    return mem[m][n];
  }
}
```
