# PRO_쇠막대기


```java


import java.io.IOException;
import java.util.*;

class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		System.out.println(s.solution("()(((()())(())()))(())"));
	}

	public int solution(String arrangement) {
		int answer = 0;

        Stack<Character> stack = new Stack<>();
        int iron = 0;
        boolean razer = true;
        
        for(int i=0; i<arrangement.length(); i++) {
        	char ch = arrangement.charAt(i);
        	if(ch=='(') {
        		stack.add(ch);
        		iron++;
        		razer = true;
        	}
        	else if(ch==')') {
        		if(stack.peek()=='(') {
        			if(!razer) {
        				answer++;
        			} else {
            			answer += (iron-1);
        			}
        			stack.pop();
        			iron--;
        			razer = false;
        		}
        	}
        }
		
		return answer;
	}
}


```

