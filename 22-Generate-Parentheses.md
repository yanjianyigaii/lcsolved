###
Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

For example, given n = 3, a solution set is:
```
[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]
```
###
Javascript

```
/**
 * @param {number} n
 * @return {string[]}
 */
var generateParenthesis = function(n) {
    var current = "";
    var result = [];
    generate(current, result, n, 0, 0);
    return result;
};

var generate = function(current, result, halfmax, open, close){
    if(current.length == halfmax*2){
        result.push(current);
        return;
    }
    if(open < halfmax){
        generate(current+'(', result, halfmax, open+1, close);
    }
    if(close < open){
        generate(current+')', result, halfmax, open, close+1);
    }
    
};
```