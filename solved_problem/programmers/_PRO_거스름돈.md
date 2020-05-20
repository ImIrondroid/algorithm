# PRO_거스름돈


```java


import java.util.*;
import java.io.IOException;


public class Solution {
	
	public static void main(String[] args) throws IOException {
		Solution s = new Solution();
		int[] money = {1,2,5};
		System.out.println(s.solution(5, money));
	}

	static final int mod = 100000007;
	
	//https://programmers.co.kr/learn/courses/30/lessons/12907
	public int solution(int n, int[] money) {
		int[] dp = new int[n+1];
		Arrays.sort(money);
		
		dp[0] = 1;
		for(int i=0; i<money.length; i++) {
			for(int j=money[i]; j<=n; j++) {
				dp[j] = dp[j] + dp[j-money[i]];
			}
		}
		
		return dp[n]%mod;
	}
}


```

