# PRO_종이접기


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		System.out.println(s.solution(4));
	}

	public int[] solution(int n) {
        String temp = "0";
        StringBuilder ret;;
        int num;
        for(int i=2; i<=n; i++) {
        	num = 0;
        	ret = new StringBuilder();
        	for(int j=0; j<temp.length(); j++) {
        		ret.append((num++)%2 + String.valueOf(temp.charAt(j)-48));
        		if(j==temp.length()-1) ret.append(String.valueOf(num%2));
        	}
        	temp = ret.toString();
        }
        
        int[] answer = new int[temp.length()];
        
        for(int i=0; i<temp.length(); i++) {
        	answer[i] = temp.charAt(i)-48;
        	//System.out.print(answer[i]+" ");
        }
        
        return answer;
    }
}


```

