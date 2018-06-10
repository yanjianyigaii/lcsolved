###
Given an array of integers nums sorted in ascending order, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order of O(log n).

If the target is not found in the array, return [-1, -1].
```
Example 1:

Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]
Example 2:

Input: nums = [5,7,7,8,8,10], target = 6
Output: [-1,-1]
```
###
Java

```
class Solution {
    int begin = Integer.MAX_VALUE;
    int end = Integer.MIN_VALUE;
    public int[] searchRange(int[] nums, int target) {
        function(nums, target, 0, nums.length-1);
        int[] result = new int[]{begin == Integer.MAX_VALUE? -1 : begin,end==Integer.MIN_VALUE?-1:end};
        return result;
    }
    
    public void function(int[] nums, int target, int left, int right){
        if(left > right){
            return;
        }
        int mid = (left+right)/2;
        if(nums[mid] == target){
            if(mid > end) end = mid;
            if(mid < begin) begin = mid;
            function(nums, target, left, mid-1);
            function(nums, target, mid+1, right);
        }else if(nums[mid]<target){
            function(nums, target, mid+1, right);
        }else{
            function(nums, target, left, mid-1);
        }
    }
}
```