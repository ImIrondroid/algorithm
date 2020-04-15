# PRO_다음 큰 숫자


```java


import java.io.IOException;
import java.util.*;

class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		System.out.println(s.solution(78));
	}

	public int solution(int n) {  
		int answer = 0;
		int nCount = 0;
	    String temp = Integer.toBinaryString(n);
	    for(int i=0; i<temp.length(); i++) {
	    	if(temp.charAt(i)=='1') nCount++;
	    }
	    for(int i=n+1; i<=1000000; i++) {
	    	int count = 0;
	    	String compare = Integer.toBinaryString(i);
	    	for(int j=0; j<compare.length(); j++) {
	    		if(compare.charAt(j)=='1') count++;
	    	}
	    	if(nCount == count) {
	    		answer = i;
	    		break;
	    	}
	    }
		return answer;
	}
}


```

