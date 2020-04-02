# PRO_시저 암호


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();

		System.out.println(solution.solution("a B z",4));
	}
	 
	public String solution(String s, int n) {
		
		String answer = "";
	     
		for(int i=0; i<s.length(); i++) {
			char temp = s.charAt(i);
			int tempCode = (int)temp;
			
			if(tempCode>=(int)'a' && (tempCode<='z')) {
				int index = tempCode+n;
				if(index>(int)'z') {
					answer+=(char)(index-26);
				} else {
					answer+=(char)index;
				}
			} else if(tempCode>=(int)'A' && (tempCode<='Z')) {
				int index = tempCode+n;
				if(index>(int)'Z') {
					answer+=(char)(index-26);
				} else {
					answer+=(char)index;
				}
			} else if(temp==' ') {
				answer+=temp;
			}
		}
		return answer;
	}
}


```

