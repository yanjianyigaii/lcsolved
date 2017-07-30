###
`medium`

You need to find the largest value in each row of a binary tree.

Example:
```
Input: 

          1
         / \
        3   2
       / \   \  
      5   3   9 

Output: [1, 3, 9]
```

###
`C#`

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
    List<int> list = new List<int>();
    public IList<int> LargestValues(TreeNode root) {
        act(root, 1);
        return list;
    }
    public void act(TreeNode node, int level){
        if(node == null){
            return;
        }
        if(list.Count < level){
            list.Add(node.val);
        }
        if(list[level-1] < node.val){
            list.RemoveAt(level-1);
            list.Insert(level-1, node.val);
        }
        act(node.left, level+1);
        act(node.right, level+1);
    }
}
```
