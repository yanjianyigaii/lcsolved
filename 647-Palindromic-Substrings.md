###
`Medium`
Given a string, your task is to count how many palindromic substrings in this string.

The substrings with different start indexes or end indexes are counted as different substrings even they consist of same characters.

Example 1:
```
Input: "abc"
Output: 3
Explanation: Three palindromic strings: "a", "b", "c".
```
Example 2:
```
Input: "aaa"
Output: 6
Explanation: Six palindromic strings: "a", "a", "a", "aa", "aa", "aaa".
```

###
Java

```
public class Solution {
    public int countSubstrings(String s) {
        boolean[][] b = new boolean[s.length()][s.length()];
        int count =0;
        char[] c = s.toCharArray();
        for(int i=c.length-1; i>=0; i--){
            for(int j=i; j< c.length; j++){
                if(c[i]==c[j] && (j-i<3||b[i+1][j-1])){
                    b[i][j] = true;
                    count++;
                }
            }
        }
        return count;
    }
}
```