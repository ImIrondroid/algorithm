# PRO_피보나치


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		System.out.println(s.solution(10000));
	}

	static int[] dp = new int[100001];
	
	//https://programmers.co.kr/learn/courses/30/lessons/12945
	public int solution(int n) {
		int[] dp = new int[n+1];
		int answer = solve(n);
		return answer;
	}
	
	public int solve(int n) {
		if(n<=1) return n;
		if(dp[n]!=0) return dp[n];
		dp[n] = solve(n-1) + solve(n-2);
		return dp[n]%1234567;
	}
}


```

