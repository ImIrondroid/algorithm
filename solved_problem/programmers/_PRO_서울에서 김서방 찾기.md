# PRO_서울에서 김서방 찾기


```java


import java.util.*;

public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();

		System.out.println(solution.solution("1234"));
	}
	
	public String solution(String[] seoul) {
		String answer = "";
		int index = 0;
		for(int i=0; i<seoul.length; i++) {
			if(seoul[i].equals("Kim")) {
				index = i;
				break;
			}
		}
	     
		return "김서방은 "+index+"에 있다";
	}
}


```

