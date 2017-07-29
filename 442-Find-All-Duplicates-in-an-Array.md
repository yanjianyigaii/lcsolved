###
Given an array of integers, 1 ≤ a[i] ≤ n (n = size of array), some elements appear twice and others appear once.

Find all the elements that appear twice in this array.

Could you do it without extra space and in O(n) runtime?

```
Example:
Input:
[4,3,2,7,8,2,3,1]

Output:
[2,3]
```

###
Java

```
public class Solution {
    public IList<int> FindDuplicates(int[] nums) {
        IList<int> list = new List<int>();
        for(int i=0; i<nums.Count(); i++){
            int current = nums[i];
            while(true){
                if(current != 0){
                    if(nums[current-1] == current&&i!=current-1){
                        list.Add(current);
                        nums[i] = 0;
                        break;
                    }
                    if(i==current-1){
                        break;
                    }
                    nums[i] = nums[current-1];
                    nums[current-1] = current;
                    current = nums[i];
                }else{
                    break;
                }
            }
        }
        return list;
    }
}
```