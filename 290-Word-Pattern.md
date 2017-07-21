###
Given a pattern and a string str, find if str follows the same pattern.

Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty word in str.

Examples:
`pattern = "abba", str = "dog cat cat dog"` should return true.
`pattern = "abba", str = "dog cat cat fish"` should return false.
`pattern = "aaaa", str = "dog cat cat dog"` should return false.
`pattern = "abba", str = "dog dog dog dog"` should return false.
Notes:
You may assume pattern contains only lowercase letters, and str contains lowercase letters separated by a single space

###
Java

```
public class Solution {
    public boolean wordPattern(String pattern, String str) {
        char[] pChars = pattern.toCharArray();
        String[] sStrings = str.trim().split("\\s+");
        if(sStrings.length != pChars.length || pattern.length() ==0 || str.length() ==0){
            return false;
        }
        HashMap<Character, String> hs = new HashMap<Character, String>();
        for(int i=0; i<pChars.length; i++){
            if(hs.containsKey(pChars[i]) && !hs.get(pChars[i]).equals(sStrings[i])){
                return false;
            }
            if(hs.containsValue(sStrings[i]) && !hs.containsKey(pChars[i])){
                return false;
            }
            hs.put(pChars[i], sStrings[i]);
        }
        return true;
    }
}
```