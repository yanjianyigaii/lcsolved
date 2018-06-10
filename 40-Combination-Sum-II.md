###
Given a collection of candidate numbers (candidates) and a target number (target), find all unique combinations in candidates where the candidate numbers sums to target.

Each number in candidates may only be used once in the combination.

Note:

All numbers (including target) will be positive integers.
The solution set must not contain duplicate combinations.
Example 1:
```
Input: candidates = [10,1,2,7,6,1,5], target = 8,
A solution set is:
[
  [1, 7],
  [1, 2, 5],
  [2, 6],
  [1, 1, 6]
]
```
Example 2:
```
Input: candidates = [2,5,2,1,2], target = 5,
A solution set is:
[
  [1,2,2],
  [5]
]
```
###
Java

```
class Solution1 {
    HashSet<List<Integer>> result = new HashSet<List<Integer>>();
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        function(candidates, 0, target, new ArrayList<Integer>());
        return new ArrayList<List<Integer>>(result);
    }
    
    public void function(int[] candidates, Integer idx, Integer current, ArrayList<Integer> currentlist){
        if(idx >= candidates.length) return;
        ArrayList<Integer> newlist = new ArrayList<Integer>(currentlist);
        int newcurrent = current - candidates[idx];
        currentlist.add(candidates[idx]);
        if(newcurrent == 0){
            Collections.sort(currentlist);
            result.add(currentlist);
        }
        if(newcurrent > 0){
            
            function(candidates, idx+1, newcurrent, currentlist);
        }
        function(candidates, idx+1, current, newlist);
    } 
}



class Solution2 {
    HashSet<List<Integer>> result = new HashSet<List<Integer>>();
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        function(candidates, 0, target, new LinkedList<Integer>());
        return new LinkedList<List<Integer>>(result);
    }
    
    public void function(int[] candidates, Integer idx, Integer current, LinkedList<Integer> list){
        if(current < 0) return;
        if(current == 0){
            Collections.sort(list);
            result.add(list);
            return;
        }
        for(int i=idx; i< candidates.length; i++){
            list.add(candidates[i]);
            LinkedList<Integer> newlist = new LinkedList<Integer>(list);
            int newcurrent = current - candidates[i];
            function(candidates, i+1, newcurrent, newlist);
            list.removeLast();
        }
    }
    
}
```

