# Queue Reconstruction by Height
Suppose you have a random list of people standing in a queue. Each person is described by a pair of integers (h, k), where h is the height of the person and k is the number of people in front of this person who have a height greater than or equal to h. Write an algorithm to reconstruct the queue.

## Note:
```
The number of people is less than 1,100.
```
## Example
```
Input:
[[7,0], [4,4], [7,1], [5,0], [6,1], [5,2]]

Output:
[[5,0], [7,0], [5,2], [6,1], [4,4], [7,1]]
```
##  Code
```
class Solution {
    public int[][] reconstructQueue(int[][] people) {
        int[][] result = new int[people.length][];
        Arrays.sort(people, new Comparator<int[]>(){
        public int compare(int[] a1, int[] a2){
            if(a1[0]!=a2[0]){
                return a2[0]-a1[0];
            }else{
                return a1[1]-a2[1];
            }
        }
    });
    ArrayList<int[]> list = new ArrayList<int[]>();
    for(int i=0; i<people.length; i++){
        int[] arr = people[i];
        list.add(arr[1],arr);
    }
    for(int i=0; i<people.length; i++){
        result[i]=list.get(i);
    }
    return result;
}
}
```

## Time Complexity
```
O(n^2)
```
