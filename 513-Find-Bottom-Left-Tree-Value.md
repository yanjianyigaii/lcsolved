###
`Medium`
Given a binary tree, find the leftmost value in the last row of the tree.
```
Example 1:
Input:

    2
   / \
  1   3

Output:
1
```

```
Example 2: 
Input:

        1
       / \
      2   3
     /   / \
    4   5   6
       /
      7

Output:
7
```

* Note: You may assume the tree (i.e., the given root node) is not NULL

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
    int max=0;
    TreeNode result = null;
    public int findBottomLeftValue(TreeNode root) {
        act(root, 1);
        return result.val;
    }
    public void act(TreeNode node, int level){
        if(node == null){
            return;
        }
        if(level > max){
            max = level;
            result = node;
        }
        act(node.left, level+1);
        act(node.right, level+1);
    }
}
```