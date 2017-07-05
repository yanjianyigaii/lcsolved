```
public class Solution {
    public int HammingDistance (int n1, int n2){
        int result = 0;
        string binary1 = getBinary(n1);
        string binary2 = getBinary(n2);
        int length1 = binary1.Length;
        int length2 = binary2.Length;
        if(length1- length2 > 0){
            binary2 = prefixZero(binary2, length1- length2);
        }else if (length1- length2 < 0){
            binary1 = prefixZero(binary1, length2- length1);
        }
        int targetLength = binary1.Length == binary2.Length ? binary1.Length : 0;
        char[] binary1Chars = binary1.ToCharArray();
        char[] binary2Chars = binary2.ToCharArray();
        for(int i = 0; i < targetLength; i++){
            char temp1 = binary1Chars[i];
            char temp2 = binary2Chars[i];
            int diff = (int)temp1 - (int)temp2;
            int abs = Math.Abs(diff);
            if(abs == 1){
                result++;
            }
        }
        return result;
    }
    public string getBinary (int number){
        int temp = number;
        StringBuilder s = new StringBuilder();
        //string binaryString = string.Empty;
        while(temp != 0){
            int c = temp%2;
            s.Insert(0, c);
            temp = temp/2;
        }
        return s.ToString();
    }
    public string prefixZero(string binary, int zeroCounts){
        for(int i = 0; i< zeroCounts; i++){
            binary = "0"+ binary;
        }
        return binary;
    }
}
```