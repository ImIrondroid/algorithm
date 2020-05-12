# PRO_소수 찾기


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();

		System.out.println(solution.solution(5));
	}
	
	//2,3,5,7
	//4,6,8,9
	 
	public int solution(int n) {
	   
		boolean visit[] = new boolean[n+1];
		int answer = 0;
		
		for(int i=2; i<=Math.sqrt(n); i++) {
			
			if(!visit[i]) {
				for(int j=i*2; j<=n; j+=i) {
					visit[j] = true;
				}
			}
		}
		
		for(int i=2; i<=n; i++) {
			if(!visit[i]) answer++;
		}
	    
		return answer;
	}
}


```

