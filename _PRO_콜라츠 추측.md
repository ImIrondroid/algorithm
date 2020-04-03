# PRO_콜라츠 추측


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();
		System.out.println(solution.solution(626331));
	}
	
	public int solution(int num) {
	   
		int answer = 0;

		while(num!=1) {
			if(num%2==0) num/=2;
			else if(num%2==1) num=(3*num)+1;
			answer++;
			if(answer>=500) break;
		}
	  
		return answer>=500? -1 : answer;
	}
}


```

