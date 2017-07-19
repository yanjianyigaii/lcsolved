###
Given a string containing just the characters *'('*, *')'*, *'{'*, *'}'*, *'['* and *']'*, determine if the input string is valid.

The brackets must close in the correct order, *"()"* and *"()[]{}"* are all valid but *"(]"* and *"([)]"* are not.

###
Java

```
public class Solution {
    public boolean isValid(String s) {
        if(s.length()==0){
            return true;
        }
        Stack<Character> stack = new Stack<Character>();
        char[] c = s.toCharArray();
        for(int i=0; i<s.length(); i++){
            if(c[i] == ')' || c[i] == ']' || c[i] == '}'){
                if(stack.size() == 0){
                    return false;
                }
                char before = stack.pop();
                if(Math.abs(c[i]-before)>2){
                    return false;
                }
            }else{
                stack.push(c[i]);    
            }
        }
        if(stack.size()!=0){
            return false;
        }
        return true;
    }
}
```