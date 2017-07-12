###
Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

For example, this binary tree `[1,2,2,3,4,4,3]` is symmetric:
```
    1
   / \
  2   2
 / \ / \
3  4 4  3
```
But the following `[1,2,2,null,3,null,3]` is not:
```
    1
   / \
  2   2
   \   \
   3    3
```

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
    public boolean isSymmetric(TreeNode root) {
        if(root== null){
            return true;
        }
        boolean b = act(root.left, root.right);
        return b;
    }
    public boolean act(TreeNode n1, TreeNode n2){
        if(n1==null && n2==null){
            return true;
        }
        if(n1==null || n2==null){
            return false;
        }
        if(n1.val != n2.val){
            return false;
        }
        return act(n1.left, n2.right) && act(n1.right, n2.left);
        
    }
}
```