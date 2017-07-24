###
Given an integer array, you need to find one continuous subarray that if you only sort this subarray in ascending order, then the whole array will be sorted in ascending order, too.

You need to find the shortest such subarray and output its length.

Example 1:
Input: `[2, 6, 4, 8, 10, 9, 15]`
Output: `5`
Explanation: You need to sort `[6, 4, 8, 10, 9]` in ascending order to make the whole array sorted in ascending order.
Note:
Then length of the input array is in range `[1, 10,000]`.
The input array may contain duplicates, so ascending order here means <=.

###
Java

```
public class Solution {
    public int findUnsortedSubarray(int[] nums) {
        int lIdx =-1;
        int rIdx =-1;
        for(int i=1; i<nums.length; i++){
            int j = nums.length-i;
            if(nums[i-1]>nums[i]){
                if(i-1<lIdx||lIdx == -1){
                    lIdx = i-1;    
                }
                if(i+1>rIdx){
                    rIdx = i+1;
                }
                int temp = nums[i-1];
                nums[i-1] = nums[i];
                nums[i] = temp;
            }
            if(nums[j]<nums[j-1]){
                if(j-1<lIdx||lIdx == -1){
                    lIdx = j-1;    
                }
                if(j+1>rIdx){
                    rIdx = j+1;
                }
                int temp = nums[j-1];
                nums[j-1] = nums[j];
                nums[j] = temp;
            }
        }
        return rIdx-lIdx;
    }
}
```