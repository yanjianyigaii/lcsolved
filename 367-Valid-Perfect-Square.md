###
Given a positive integer num, write a function which returns True if num is a perfect square else False.

Note: Do not use any built-in library function such as sqrt.

Example 1:

Input: 16
Returns: True

Example 2:

Input: 14
Returns: False

###
Java

```
public class Solution {
    public bool IsPerfectSquare(int num) {
        int start = 1;
        while(start <= num/start){
            int rest = num/start;
            if(rest == start && num%start==0){
                return true;
            }
            start++;
        }
        return false;
    }
}
```