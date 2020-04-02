# PRO_수박수박수박수박수박수


```java


import java.util.*;

public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();

		System.out.println(solution.solution(5));
	}
	 
	public String solution(int n) {
	     
		String answer = "";
	    String word = "수박";
	    String halfword = "수";
		if(n==1) {
			answer=halfword;
		} else {
			for(int i=0; i<n/2; i++) {
				answer+=word;
			}
			if(n%2==1) {
				answer+=halfword;
			}
		}
		return answer;
	}
}


```

