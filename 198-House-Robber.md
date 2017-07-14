###
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

For example:
`[1,2,11,5,6,8,3,7]`
###
Java

```
public class Solution {
    public int rob(int[] nums) {
        int[] m = new int[nums.length];
        int max = 0;
        for(int i=0; i<nums.length; i++){
            int temp = 0;
            m[i] = nums[i];
            max = Math.max(m[i], max);
            for(int j=i-2; j>=0; j--){
                temp = Math.max(temp, m[j]);
                m[i] = temp + nums[i];
                max = Math.max(m[i], max);
            }
        }
        return max;
    }
}
```