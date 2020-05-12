# PRO_짝지어 제거하기


```java


import java.util.*;


class Solution {

	public static void main(String[] args) {
		
		//https://programmers.co.kr/learn/courses/30/lessons/62048
		Solution solution = new Solution();
		System.out.println(solution.solution("baabaa"));
	}
	
	public int solution(String s)
    {
        int answer = 0;

        Stack<Character> stack = new Stack<>();
        
        for(int i=0; i<s.length(); i++) {
        	if(!stack.isEmpty()) {
        		if(s.charAt(i)==stack.peek()) stack.pop();
        		else stack.add(s.charAt(i));
        	} else {
        		stack.add(s.charAt(i));
        	}
        }
        
        if(stack.isEmpty()) return 1;
        else return 0;
    }
}


```

