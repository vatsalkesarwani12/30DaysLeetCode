# Power of Two
Given an integer, write a function to determine if it is a power of two.

## Example 1:
```
Input: 1
Output: true 
Explanation: 20 = 1
```
## Example 2:
```
Input: 16
Output: true
Explanation: 24 = 16
```
## Example 3:
```
Input: 218
Output: false
```
## Code
```
class Solution {
    public boolean isPowerOfTwo(int n) {
        if(n>0){
            int a=(int)Math.floor(Math.log(n)/Math.log(2));
            if(n%(int)Math.pow(2,a)==0){
                return true;
            }
            else return false;
        }
        else return false;
    }
}
```
## Time Complexity
```
O(1)
```
