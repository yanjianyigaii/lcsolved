** java medium solution
```
public class Solution {
    public String addStrings(String num1, String num2) {
        //add leading zero;
        int length = Math.max(num1.length(), num2.length());
        StringBuilder num1SB = addLeadingZero(num1, length);
        StringBuilder num2SB = addLeadingZero(num2, length);
        char[] A = num1SB.toString().toCharArray();
        char[] B = num2SB.toString().toCharArray();
        ResultSet resultSet = add(A, B, 0, 0);
        int[] result = new int[resultSet.s.size()];
        StringBuilder sb = new StringBuilder();
        while(!resultSet.s.empty()){
            sb.append(resultSet.s.pop());
        }
        return sb.toString();
    }
    public ResultSet add(char[] A, char[] B, int idxA, int idxB){
        if(idxA == A.length || idxB == B.length){
            return new ResultSet();
        }
        ResultSet prev = add(A, B, idxA+1, idxB+1);
        int sum = (A[idxA]-48 + B[idxB]-48+ prev.carry)%10;
        int carry = (A[idxA]-48 + B[idxB]-48+ prev.carry)/10;
        prev.carry = carry;
        prev.add(sum);
        if(carry ==1 && idxA ==0){
            prev.add(1);
        }
        ResultSet current = prev;
        return current;
    }
    public StringBuilder addLeadingZero(String num, int length){
        StringBuilder sb = new StringBuilder(num);
        if(sb.length()<length){
            sb.insert(0,'0');
        }
        return sb;
    }
    
    public class ResultSet {
        int carry;
        Stack<Integer> s;
        public ResultSet(){
            if(s == null){
                s = new Stack<Integer>();    
            }
        }
        public void add(int sum){
            s.push(sum);
        }
    }
}
```

**java easy solution
```
public class Solution {
    public String addStrings(String num1, String num2) {
        int length = Math.max(num1.length(), num2.length());
        StringBuilder sb1 = addLeadingZero(num1, length);
        StringBuilder sb2 = addLeadingZero(num2, length);
        char[] charnum1 = sb1.toString().toCharArray();
        char[] charnum2 = sb2.toString().toCharArray();  
        StringBuilder sb = new StringBuilder();
        int carry = 0;
        for(int i= length-1; i>=0; i--){
            if(charnum1.length == charnum2.length){
                int sum = 
                    (charnum1[i]-48+charnum2[i]-48+carry)%10;
                carry = 
                    (charnum1[i]-48+charnum2[i]-48+carry)/10;
                sb.insert(0, sum);
                if(i==0 && carry ==1){
                    sb.insert(0, '1');
                }
            }
        }
        return sb.toString();
    }
    public StringBuilder addLeadingZero(String num, int length){
        StringBuilder sb = new StringBuilder(num);
        while(sb.length()<length){
            sb.insert(0,'0');
        }
        return sb;
    }
}
```
