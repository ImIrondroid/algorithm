# PRO_문자열 내림차순으로 배치하기


```java


import java.util.*;

public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();

		System.out.println(solution.solution("Zbcdefg"));
	}
	
	public String solution(String s) {

		String answer = "";
		char temp = '0';
	     
		char[] alphabet = new char[s.length()];
		
		for(int i=0; i<alphabet.length; i++) {
			alphabet[i] = s.charAt(i);
		}
		
		//대문자 맨 뒤로 보내기
		for(int i=0; i<s.length()-1; i++) {
			for(int j=0; j<s.length()-i-1; j++) {
				if((int)alphabet[j]<(int)alphabet[j+1]) {
					temp = alphabet[j+1];
					alphabet[j+1] = alphabet[j];
					alphabet[j] = temp;
				} 
			}
		}
		
		for(int i=0; i<s.length(); i++) {
			answer+=(alphabet[i]);
		}
		
		return answer;
	}
}


```

