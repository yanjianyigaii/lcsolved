###
Given a binary tree, return all root-to-leaf paths.

For example, given the following binary tree:
```
   1
 /   \
2     3
 \
  5
```
All root-to-leaf paths are:

`["1->2->5", "1->3"]`

###
Java
```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     public int val;
 *     public TreeNode left;
 *     public TreeNode right;
 *     public TreeNode(int x) { val = x; }
 * }
 */
public class Solution {
    IList<string> list = new List<string>();
    public IList<string> BinaryTreePaths(TreeNode root) {
        if(root != null){
            Act(root,root.val.ToString());
        }
        return list;
    }
    public void Act(TreeNode root, string s){

        if(root.left == null && root.right== null){
            list.Add(s);
        }
        if(root.left != null){
            Act(root.left, s + "->" + root.left.val.ToString());
        }
        if(root.right != null){
            Act(root.right, s + "->" + root.right.val.ToString());
        }
    }
}
```