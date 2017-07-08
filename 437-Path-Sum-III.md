###
You are given a binary tree in which each node contains an integer value.

Find the number of paths that sum to a given value.

The path does not need to start or end at the root or a leaf, but it must go downwards (traveling only from parent nodes to child nodes).

The tree has no more than 1,000 nodes and the values are in the range -1,000,000 to 1,000,000.

Example:
```
root = [10,5,-3,3,2,null,11,3,-2,null,1], sum = 8

      10
     /  \
    5   -3
   / \    \
  3   2   11
 / \   \
3  -2   1

Return 3. The paths that sum to 8 are:

1.  5 -> 3
2.  5 -> 2 -> 1
3. -3 -> 11
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
    List<Integer[]> lists;
    Integer sum=0;
    public int pathSum(TreeNode root, int sum) {
        this.sum = sum;
        lists = new ArrayList<Integer[]>();
        Integer[] path = new Integer[1000];
        actPathSum(root, path, 0);
        return lists.size();
    }
    public void actPathSum(TreeNode root, Integer[] path, int level){
        if(root == null){
            return;
        }
        path[level] = root.val;
        int temp =0;
        for(int i=level; i>=0; i--){
            temp += path[i];
            if(temp == sum){
                lists.add(path);
            }
        }
        actPathSum(root.left, path, level+1);
        actPathSum(root.right, path, level+1);
    }
}
```