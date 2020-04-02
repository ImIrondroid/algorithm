# PRO_약수의 합


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();

		System.out.println(solution.solution(12));
	}
	 
	public int solution(int n) {
		 
		int answer = 0;
			
		for(int i=1; i<=n/2; i++) {
			if(n%i==0) answer+=i;
		}
		
		return answer+n;
	}
}


```

