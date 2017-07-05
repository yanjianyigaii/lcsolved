## C# easy solution

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
    public TreeNode MergeTrees(TreeNode t1, TreeNode t2) {
        TreeNode node = null;
        if(t1 == null && t2 == null){
            return node;
        }
        else if(t1== null){
            node = new TreeNode(t2.val);
        }
        else if(t2==null){
            node = new TreeNode(t1.val);
        }
        else{
            node = new TreeNode(t1.val + t2.val);
        }

        node.left = MergeTrees(t1!=null?t1.left:null, t2!=null?t2.left:null);
        node.right = MergeTrees(t1!=null?t1.right:null, t2!=null?t2.right:null);
        return node;
    }
}
```