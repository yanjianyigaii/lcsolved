###
Given an array of strings, group anagrams together.

Example:
```
Input: ["eat", "tea", "tan", "ate", "nat", "bat"],
Output:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]
```
Note:

All inputs will be in lowercase.
The order of your output does not matter.
###
Java

```
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        List<List<String>> result = new ArrayList<>();
        HashMap<String, ArrayList<String>> hashmap = new HashMap<String, ArrayList<String>>();
        for(int i=0; i<strs.length; i++){
            char[] temp = strs[i].toCharArray();
            Arrays.sort(temp);
            String s = new String(temp);
            if(!hashmap.containsKey(s)){
                ArrayList<String> list = new ArrayList<String>();
                hashmap.put(s, list);
            }
            hashmap.get(s).add(strs[i]);
        }
        for (Map.Entry<String, ArrayList<String>> entry : hashmap.entrySet()) {
            result.add(entry.getValue());
        }
        return result;
    }
}
```

