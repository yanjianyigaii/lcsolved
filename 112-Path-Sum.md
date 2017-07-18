###
Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

For example:
Given the below binary tree and sum = 22,
```
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \      \
        7    2      1
```
return true, as there exist a root-to-leaf path `5->4->11->2` which sum is `22`.

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
    boolean result;
    public boolean hasPathSum(TreeNode root, int sum) {
        act(root, sum, 0);
        return result;
    }
    public void act(TreeNode node, int sum, int current){
        if(node == null){
            return;
        }
        current += node.val;
        if(current == sum && node.left == null && node.right == null){
            result = true;
        }
        act(node.left, sum, current);
        act(node.right, sum, current);
    }
}
```