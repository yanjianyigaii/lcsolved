###
Given a binary tree, determine if it is height-balanced.

For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

###
Java

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
    public boolean isBalanced(TreeNode root) {
        int balanceNum = act(root);
        if(balanceNum == -1){
            return false;
        }
        return true;
    }
    public int act(TreeNode node){
        if(node == null){
            return 0;
        }
        int left = act(node.left);
        if(left == -1){
            return -1;
        }
        int right = act(node.right);
        if(right == -1){
            return -1;
        }
        int diff = Math.abs(left-right);
        if(diff > 1){
            return -1;
        }
        int height = Math.max(left, right)+1;
        return height;
    }
}
```
