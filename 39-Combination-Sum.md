###
Given a set of candidate numbers (candidates) (without duplicates) and a target number (target), find all unique combinations in candidates where the candidate numbers sums to target.

The same repeated number may be chosen from candidates unlimited number of times.

Note:

All numbers (including target) will be positive integers.
The solution set must not contain duplicate combinations.
Example 1:
```
Input: candidates = [2,3,6,7], target = 7,
A solution set is:
[
  [7],
  [2,2,3]
]
```
Example 2:
```
Input: candidates = [2,3,5], target = 8,
A solution set is:
[
  [2,2,2,2],
  [2,3,3],
  [3,5]
]
```
###
C#

```
public class Solution {
    IList<IList<int>> resultList = new List<IList<int>>();
    public IList<IList<int>> CombinationSum(int[] candidates, int target) {
        Array.Sort(candidates);
        function(target, 0, new List<int>(), candidates, 0);
        return resultList;
    }
    
    public void function(int current, int idx, IList<int> currentList,  int[] candidates, int i){
        if(idx >= candidates.Length){
            return;
        } 
        var newList = new List<int>(currentList);
        int newcurrent = current - candidates[idx];
        
        if(newcurrent < 0){
            return;
        }
        currentList.Add(candidates[idx]);
        if(newcurrent == 0) {
            resultList.Add(currentList);
            return;
        }
        if(newcurrent > 0){
            
            function(newcurrent, idx,currentList,candidates, i+1);
            function(current, idx+1, newList, candidates, i);
        }
    }
}
```