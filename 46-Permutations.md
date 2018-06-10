###
Given a collection of distinct integers, return all possible permutations.

Example:
```
Input: [1,2,3]
Output:
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```
###
Java

```
class Solution {
    List<List<Integer>> result = new ArrayList<>();
    public List<List<Integer>> permute(int[] nums) {
        function(0, nums, new ArrayList<Integer>());
        return result;
    }
    
    public void function(int idx, int[] nums, ArrayList<Integer> list){
        if(list.size() == nums.length){
            result.add(list);
        }else{
            for(int i=0; i<nums.length; i++){
                if(list.contains(nums[i])) continue;
                list.add(nums[i]);
                ArrayList<Integer> newlist = new ArrayList<Integer>(list);
                int newi=i+1;
                if(i==nums.length-1){
                    newi=0;
                }
                function(newi, nums, newlist);
                list.remove(list.size() - 1);
            }
        }
       // if(list.size() == nums.length){
       //    result.add(new ArrayList<>(list));
       // } else{
       //    for(int i = 0; i < nums.length; i++){ 
       //      if(list.contains(nums[i])) continue;
       //      list.add(nums[i]);
       //      function(nums, list);
       //      list.remove(list.size() - 1);
       //    }
       // }
    }
}
```

