# PRO_정수 제곱근 판별


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();

		System.out.println(solution.solution(14443*14443));
	}
	
	public long solution(long n) {
	      
		long answer = 0;
	    long num = 0;
		for(int i=1; i<=14000000; i++) {
			long pow = (long)i*(long)i;
			if(pow>n) break;
			else {
				if(pow==n) {
					num = (i+1);
					break;
				}
			}
		}
		
		if(num==0) {
			return -1;
		} else {
			return num*num;
		}
	}
}


```

