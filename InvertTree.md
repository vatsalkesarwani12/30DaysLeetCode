# Approach (Recursive) [Accepted]
This is a classic tree problem that is best-suited for a recursive approach.

# Algorithm

The inverse of an empty tree is the empty tree. The inverse of a tree with root rr, and subtrees \mbox{right} and \mbox{left}, is a tree with root rr, whose right subtree is the inverse of \mbox{left}, and whose left subtree is the inverse of \mbox{right}.

### Java
```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public TreeNode invertTree(TreeNode root) {
        if(root == null){
            return root;
        }

        TreeNode left = invertTree(root.left); 
        TreeNode right = invertTree(root.right); 
  
        root.left = right; 
        root.right = left; 
  
        return root; 
    }
}
```
### Complexity Analysis

Since each node in the tree is visited only once, the time complexity is O(n)O(n), where nn is the number of nodes in the tree. We cannot do better than that, since at the very least we have to visit each node to invert it.

Because of recursion, O(h)O(h) function calls will be placed on the stack in the worst case, where hh is the height of the tree. Because h\in O(n)h∈O(n), the space complexity is O(n)O(n).

