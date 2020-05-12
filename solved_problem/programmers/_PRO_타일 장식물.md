# PRO_타일 장식물


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		System.out.println(s.solution(6));
	}

	public long solution(int N) {
       
        int a = 1;
        int b = 1;
        
        for(int i=3; i<=N+1; i++) {
        	//System.out.print(a+" "+b+" -> ");
        	int temp = b;
        	b = a + b;
        	a = temp;
        	//System.out.println(a+" "+b);
        }
        
        return 2*a+2*b;
    }
}


```

