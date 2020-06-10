# Search Insert Position
Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.

## Example 1:
```
Input: [1,3,5,6], 5
Output: 2
```
## Example 2:
```
Input: [1,3,5,6], 2
Output: 1
```
## Example 3:
```
Input: [1,3,5,6], 7
Output: 4
```
## Example 4:
```
Input: [1,3,5,6], 0
Output: 0
```
## Code
```
class Solution {
    public int searchInsert(int[] nums, int target) {
        int f=0;
        int l=nums.length-1;
        int mid=0;
        while(f<=l){
            mid=(f+l)/2;
                if(target>nums[mid]){
                    f=mid+1;
                }
                else if(target<nums[mid]) {
                    l=mid-1;
                }
                else return mid;
        }
        return f;
    }
}
```

## Time Complexity
```
O(log n)
```
