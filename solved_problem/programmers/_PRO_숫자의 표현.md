# 숫자의 표현


```java


import java.io.IOException;
import java.util.*;

class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		System.out.println(s.solution(15));
	}

	public int solution(int n) {
		
	    int answer = 0;
	    
	    for(int i=1; i<=n/2; i++) {
	    	int sum = 0;
	    	Loop : for(int j=i; j<=n/2+1; j++) {
	    		sum += j;
	    		if(sum > n) break Loop;
	    		if(sum == n) {
	    			answer++;
	    			break Loop;
	    		}
	    	}
	    }
	    
	    return answer+1;
	}
}


```

