###
`Medium`
Given a circular array (the next element of the last element is the first element of the array), print the Next Greater Number for every element. The Next Greater Number of a number x is the first greater number to its traversing-order next in the array, which means you could search circularly to find its next greater number. If it doesn't exist, output -1 for this number.

Example 1:
Input: `[1,2,1]`
Output: `[2,-1,2]`
Explanation: The first 1's next greater number is 2; 
The number 2 can't find next greater number; 
The second 1's next greater number needs to search circularly, which is also 2.
Note: The length of given array won't exceed 10000.

###
`Javacript`

```
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var nextGreaterElements = function(nums) {
    var result = nums.slice(0);
    for(var i=0; i<nums.length; i++){
        var before = 0;
        var after = i+1;
        while((before>=0&&before<=i)||after<nums.length){
            if(before>=0 && nums[before]>nums[i]){
                if(after>=nums.length){
                    result[i] = nums[before];
                    break;
                }
            }else{
                before++;
            }
            if(after<nums.length && nums[after]>nums[i]){
                result[i] = nums[after];
                break;
            }else{
                after++;
            }
        }
        if(before>i && after>=nums.length){
            result[i] = -1;
        }
    }
    return result;
};
```