###
Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent.

A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

Example:
```
Input: "23"
Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
```

Note:
Although the above answer is in lexicographical order, your answer could be in any order you want.

###
Javascript

```
/**
 * @param {string} digits
 * @return {string[]}
 */
var letterCombinations = function(digits) {
    if (digits.length ==0){
        return [];
    }
    var dict = {2: "abc", 3: "def", 4: "ghi", 5: "jkl", 6: "mno", 7: "pqrs", 8: "tuv", 9: "wxyz"};
    var s = "";
    var result = [];
    recursion(digits, 0, s, result, dict);
    return result;
};

var recursion = function(digits, idx, s, result, dict){
    if (idx > digits.length-1){
        result.push(s);
        return;
    }
    var num = digits.charAt(idx);
    
    var values = dict[num];
    for (var i=0; i<values.length; i++){
        var current = s;
        current += values.charAt(i);
        recursion(digits, idx+1, current, result, dict);
    }
};
```