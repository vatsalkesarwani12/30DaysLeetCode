# Single Number II
Given a non-empty array of integers, every element appears three times except for one, which appears exactly once. Find that single one.

## Note:

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

## Example 1:
```
Input: [2,2,3,2]
Output: 3
```
## Example 2:
```
Input: [0,1,0,1,0,1,99]
Output: 99
```
## Code
```
class Solution {
    public int singleNumber(int[] nums) {
        int one = 0;
        int two = 0;
        int three = 0;
        for (int i = 0; i < nums.length; i ++){
            two = two | ( one & nums[i]);
            one = one ^ nums[i];
            three = one & two;
            one = one & (~three);
            two = two & (~three);
        }//for
        return one;
    }
}
```
## Time Complexity
```
O(N)
```
