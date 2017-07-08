###
Given a binary tree, return the bottom-up level order traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).

For example:
Given binary tree [3,9,20,null,null,15,7],
```
    3
   / \
  9  20
    /  \
   15   7
```
return its bottom-up level order traversal as:
```
[
  [15,7],
  [9,20],
  [3]
]
```

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
    List<List<Integer>> lists;
    public List<List<Integer>> levelOrderBottom(TreeNode root) {
        lists = new LinkedList<List<Integer>>();
        actLevel(root,0);
        return lists;
    }
    public void actLevel(TreeNode node, int level){
        if(node == null){
            return;
        }
        List<Integer> list = new LinkedList<Integer>();
        if(lists.size() <= level){
            lists.add(0,list); //insert list to lists at index 0
        }
        lists.get(lists.size()-1-level).add(node.val);
        actLevel(node.left, level+1);
        actLevel(node.right, level+1);
    }
}

```