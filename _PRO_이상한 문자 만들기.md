# PRO_이상한 문자 만들기


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();

		System.out.println(solution.solution(" try hello worl d    "));
	}
	 
	public String solution(String s) {
	    
		String[] arr = s.split(" ",-1);
		String answer = "";
		
		for(int i=0; i<arr.length; i++) {
			String temp = arr[i];
			if(temp.equals(" ")) {
				answer+=" ";
			} else {
				for(int j=0; j<temp.length(); j++) {
					int alphatempCode = (int)temp.charAt(j);		
					//짝수
					if((j+1)%2==1) {
						if(alphatempCode>='a' && alphatempCode<='z') {
							answer+=(char)(alphatempCode-32);
						} else {
							answer+=(char)(alphatempCode);
						}
					} else {
						//홀수
						if(alphatempCode>='A' && alphatempCode<='Z') {
							answer+=(char)(alphatempCode+32);
						} else {
							answer+=(char)(alphatempCode);
						}
					}
				}
				if(i!=arr.length-1) answer+=" ";
			}
		}
	   	return answer;
	}
}


```

