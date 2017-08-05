###
`Medium`
Given a non-empty array of integers, return the k most frequent elements.

For example,
Given `[1,1,1,2,2,3]` and `k = 2`, return `[1,2]`.

Note: 
You may assume k is always valid, 1 ? k ? number of unique elements.
Your algorithm's time complexity must be better than O(n log n), where n is the array's size.

###
Java
```
public class Solution {
    public List<Integer> topKFrequent(int[] nums, int k) {
        List<Integer> list = new LinkedList<Integer>();
        HashMap<Integer, Integer> hs = new HashMap<Integer, Integer>();
        int max = 0;
        for(int i=0; i<nums.length; i++){
            Integer count = 1;
            if(hs.containsKey(nums[i])){
                count = hs.get(nums[i]);
                count++;
                hs.remove(nums[i]);
            }
            hs.put(nums[i], count);
            if(count>max){
                max = count;
            }
        }
        int currentMax = max;
        int currentK = k;
        while(currentMax>0 && currentK>0){
            for(Map.Entry<Integer, Integer> entry : hs.entrySet()){
                Integer key=entry.getKey();
                Integer value=entry.getValue();
                if(value==currentMax){
                    list.add(key);
                    currentK--;
                    if(currentK==0){
                        break;
                    }
                }
            }
            currentMax--;
        }
        return list;
    }
}
```