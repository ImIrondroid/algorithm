# PRO_최대공약수와 최소공배수


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();
		
		//https://programmers.co.kr/learn/courses/30/lessons/64064
		System.out.println(solution.solution(3,12));
	}
	
	public int[] solution(int n, int m) {
	      int[] answer = new int[2];
	      
	      answer[0] = gcd(n,m);
	      answer[1] = (n*m)/answer[0];
	      
	      return answer;

	}
	
	public int gcd(int n, int m) {

		if(n%m == 0) return m;
		else return gcd(m, n%m);
	}
}


```

