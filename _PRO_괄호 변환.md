# PRO_괄호 변환


```java


import java.io.IOException;
import java.util.*;

class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		System.out.println(s.solution("()))((()"));
	}

	public String solution(String p) {
        String answer = "";
		
		if(p.length()==0) return "";
		
		if(check(p)) {
			return p;
		} else {
			String temp = p.toString();
			answer = process(temp);
		}

        return answer;
    }
	
	public String process(String str) {
		if(str.length()==0) return "";
		String u = "";
		String v = "";
		int left = 0;
		int right = 0;
		for(int i=0; i<str.length(); i++) {
			if(str.charAt(i)=='(') left++;
			else if(str.charAt(i)==')') right++;	
			if(left>0 && right>0 && left==right) {
				u = str.substring(0, left+right);
				v = "";
				if(left+right!=str.length()) v = str.substring(left+right, str.length());
				break;
			}
		}
		if(check(u)) {
			return u + process(v);
		} else {
			String temp = "";
			for(int i=1; i<u.length()-1; i++) {
				if(u.charAt(i)=='(') temp += ')';
				else if(u.charAt(i)==')') temp += '(';
			}
			return "("+process(v)+")"+temp;
		}
	}

	public boolean check(String u) {
		Stack<Character> stack = new Stack<>();
		for(int i=0; i<u.length(); i++) {
			if(u.charAt(i)=='(') {
				stack.add('(');
			} else if(u.charAt(i)==')') {
				if(stack.isEmpty()) return false;
				if(stack.peek()=='(') {
					stack.pop();
				}
			}
		}
		if(stack.size()>0) return false;
		return true;
	}
}


```

