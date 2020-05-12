# PRO_자릿수 더하기


```java


import java.util.*;

public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();

		System.out.println(solution.solution(123456789));
	}
	
	public int solution(int n) {
        int answer = 0;

        while(n>0) {
        	answer+=(n%10);
        	n/=10;
        }

        return answer;
    }
}


```

