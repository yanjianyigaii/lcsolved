###
`Medium`
Given a sorted array consisting of only integers where every element appears twice except for one element which appears once. Find this single element that appears only once.
```
Example 1:
Input: [1,1,2,3,3,4,4,8,8]
Output: 2
```

```
Example 2:
Input: [3,3,7,7,10,11,11]
Output: 10
```
Note: Your solution should run in O(log n) time and O(1) space.

###
C#
```
public class Solution {
    int result = 0;
    public int SingleNonDuplicate(int[] nums) {
        act(nums, 0, nums.Length-1);
        return result;
    }
    public void act(int[] nums, int left, int right){
        if(left>right){
            return; 
        }
        int mid = (left+right)/2;
        if((mid==0 || nums[mid-1]!=nums[mid]) && (mid==nums.Length-1 || nums[mid+1]!=nums[mid])){
            result = nums[mid];
            return;
        }
        act(nums, mid+1, right);
        act(nums, left, mid-1);
    }
}
```