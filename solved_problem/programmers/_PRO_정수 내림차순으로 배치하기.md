# PRO_정수 내림차순으로 배치하기


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();

		long n = 118372L;
		System.out.println(solution.solution(n));
	}
	
	public long solution(long n) {
	    
		String[] arr = String.valueOf(n).split("");
		String temp = "";
		
		for(int i=0; i<arr.length-1; i++) {
			for(int j=0; j<arr.length-i-1; j++) {
				if(Integer.valueOf(arr[j])<Integer.valueOf(arr[j+1])) {
					temp = arr[j+1];
					arr[j+1] = arr[j];
					arr[j] = temp;
				}
			}
		}
		
		temp=" ";
		
		for(int i=0; i<arr.length; i++) {
			temp+=arr[i];
		}
		
		long answer = Long.valueOf(temp);
	    
		return answer;
	  
	}
}


```

