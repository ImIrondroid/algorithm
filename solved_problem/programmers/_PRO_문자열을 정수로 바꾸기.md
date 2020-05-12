# PRO_문자열을 정수로 바꾸기


```java


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();
		
		System.out.println(solution.solution("-1234"));
	}
	
	public int solution(String s) {
	
		int answer = 0;
		char operator = s.charAt(0);
		if(operator=='-') {
			answer = (-1)*Integer.valueOf(s.substring(1, s.length()));
		} else {
			answer = Integer.valueOf(s);
		}
      
		return answer;
	}
}


```

