### Given a binary tree, you need to compute the length of the diameter of the tree. The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.

Example:
Given a binary tree 
```
          1
         / \
        2   3
       / \     
      4   5
```
Return 3, which is the length of the path [4,2,1,3] or [5,2,1,3].

### Java
```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Solution {
    public int diameter;
    public int diameterOfBinaryTree(TreeNode root) {
        int treeLength = lengthDiameter(root);
        return diameter;
        
    }
    public int lengthDiameter(TreeNode node){
        if(node == null){
            return 0;
        }
        int l = lengthDiameter(node.left);
        int r = lengthDiameter(node.right);
        int length = Math.max(l,r)+1;
        int d = l+r;
        if(diameter < d){
            diameter = d;
        }
        return length;
    }
}
```