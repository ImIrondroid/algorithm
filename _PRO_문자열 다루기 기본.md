# PRO_문자열 다루기 기본


```java


import java.util.*;

public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();

		System.out.println(solution.solution("1234"));
	}
	
	public boolean solution(String s) {
		
		boolean answer = true;
		
		if(s.length()==4 || s.length()==6) {
			for(int i=0; i<s.length(); i++) {
				if((int)s.charAt(i)<(int)'0' || (int)s.charAt(i)>(int)'9') {
					answer = false;
					break;
				}
			}
		} else {
			answer = false;
		}
		
		return answer;
	}
}


```

