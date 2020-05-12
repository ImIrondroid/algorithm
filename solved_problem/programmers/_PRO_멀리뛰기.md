# PRO_멀리뛰기


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		System.out.println(s.solution(10));
	}

	int[] dp = new int[2001];
	
	public long solution(int n) {
	
		long answer = 0;
	    
		//111
		//21
		//12
		
		//1111
		//211
		//121
		//112
		//22
		
		//11111
		//2111
		//1211
		//1121
		//1112
		//221
		//212
		//122
		
		//111111
		//21111
		//12111
		//11211
		//11121
		//11112
		//2211
		//2121
		//2112
		//1221
		//1212
		//1122
		//222
		
		dp[0] = 1;
		dp[1] = 1; 
		
		for(int i=2; i<=n; i++) {
			dp[i] = dp[i-1]%1234567 + dp[i-2]%1234567;
			System.out.print(dp[i]+"  ");
		}
		
		return answer;
	}
}


```

