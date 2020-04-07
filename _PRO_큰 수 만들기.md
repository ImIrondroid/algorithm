# PRO_큰 수 만들기


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		
		System.out.println(s.solution("417752841", 8));
	}
	
	public String solution(String number, int k) {
        
		int count = 0;
		String answer = "";
		Stack<Integer> stack = new Stack<>();
		
		for(int i=0; i<number.length(); i++) {
			int num = number.charAt(i)-48;
			while(!stack.isEmpty()) {
				if(count==k) break;
				if(stack.peek()>=num) break;
				else {
					int pop = stack.pop();
					count++;
				}
			}
			stack.push(num);
		}
		
		while(stack.size() != (number.length()-k)) {
			stack.pop();
		}
		
		for(int i=0; i<number.length()-k; i++) {
			int num = stack.pop();
			answer = String.valueOf(num) + answer;
		}
		
        return answer;
    }
}


```

