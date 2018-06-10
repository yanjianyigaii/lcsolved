###


Given an array nums of n integers and an integer target, find three integers in nums such that the sum is closest to target. Return the sum of the three integers. You may assume that each input would have exactly one solution.

Example:

Given array nums = [-1, 2, 1, -4], and target = 1.

The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
###
Javascript

```
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var threeSumClosest = function(nums, target) {
    
    var dif = Number.MAX_VALUE;
    var res = 0;
    nums.sort((a,b)=> a-b);
    for(var i=0; i< nums.length-2; i++){
        if(i>0 && nums[i] == nums[i-1]){
            continue;
        }
        for(var j=i+1, k=nums.length-1; j<k;){
            var sum = nums[i]+nums[j]+nums[k];
            var abs = Math.abs(sum-target);
            var prev = dif;
            dif = Math.min(prev, abs);
            res = dif < prev? sum: res;
            if(sum < target){
                j++;
                while(j<k && nums[j]==nums[j-1]){
                    j++;
                }
            }
            else if(sum>target){
                k--;
                while(j<k && nums[k]==nums[k+1]){
                    k--;
                }
            }
            else{
                j++;
                k--;         
            }
        }
    }
    return res;
};
```