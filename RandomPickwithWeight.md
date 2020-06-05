# Random Pick with Weight
Given an array w of positive integers, where w[i] describes the weight of index i, write a function pickIndex which randomly picks an index in proportion to its weight.

## Note:
```
1. 1 <= w.length <= 10000
2. 1 <= w[i] <= 10^5
3. pickIndex will be called at most 10000 times.
```
## Example 1:
```
Input: 
["Solution","pickIndex"]
[[[1]],[]]
Output: [null,0]
```
## Example2: 
```
Input: 
["Solution","pickIndex","pickIndex","pickIndex","pickIndex","pickIndex"]
[[[1,3]],[],[],[],[],[]]
Output: [null,0,1,1,1,0]
```
## Explanation of Input Syntax:

The input is two lists: the subroutines called and their arguments. Solution's constructor has one argument, the array w. pickIndex has no arguments. Arguments are always wrapped with a list, even if there aren't any.
## Code
```
class Solution {  
    int[] arr;
    int max = 0;
    Random random = new Random();
    public Solution(int[] w) {
        int[] arr = new int[w.length];
        arr[0] = w[0];
        max += w[0];
        for(int i=1; i<w.length; i++){
            arr[i] = arr[i-1] + w[i];
            max+=w[i];
        }
        this.arr = arr;
    }
    
    public int pickIndex() {
        int rnd = random.nextInt(max) + 1; 
        int ret = Arrays.binarySearch(arr, rnd); 
        if(ret < 0) ret = -ret - 1; 
        return ret;
    }
}

/**
 * Your Solution object will be instantiated and called as such:
 * Solution obj = new Solution(w);
 * int param_1 = obj.pickIndex();
 */
 ```
