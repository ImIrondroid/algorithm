# PRO_두 정수 사이의 합


```java


import java.util.*;

public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();
		int arr[] = {5,9,7,10};
		System.out.println(solution.solution(10000000,0));
	}
	
	 public long solution(int a, int b) {
	   
		 long answer = 0;
	   
		 if(a==b) return a;
		 else {
			if(a>b) {
				answer =  (((long)a*(long)(a+1))/2)-(((long)b*(long)(b-1))/2);
 			} else {
				answer = (((long)b*(long)(b+1))/2)-(((long)a*(long)(a-1))/2);
			}
			 
			 return answer;
		 }
	 }
}


```

