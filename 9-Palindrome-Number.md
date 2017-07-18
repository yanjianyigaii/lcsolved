###
Determine whether an integer is a palindrome. Do this without extra space.

###
Java

```
public class Solution {
    public boolean isPalindrome(int x) {
        String s = new Integer(x).toString();
        char[] c = s.toCharArray();
        int mid = s.length()/2;
        int rest = s.length()%2;
        int left = mid-1;
        int right = rest == 1? mid+1 : mid;

        while(left>=0 && right<s.length()){
            if(c[left--] != c[right++]){
                return false;
            }
        }
        if(left<0&&right>=s.length()){
            return true;
        }
        return false;
    }
}
```