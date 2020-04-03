# PRO_[1차] 비밀지도


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();
		int[] arr1 = {46,33,33,22,31,50};
		int[] arr2 = {27,56,19,14,14,10};
		System.out.println(solution.solution(6, arr1, arr2));
	}
	
	public String[] solution(int n, int[] arr1, int[] arr2) {     
		String[] answer = new String[n];
		int[] temp = new int[n];
		for(int i=0; i<n; i++) {
			temp[i] = arr1[i] | arr2[i];
			answer[i] = numToWall(temp[i], n);
		}
		
		for(int i=0; i<n; i++) {
			System.out.println(answer[i]);
		}
		
		return answer;
	}
	
	public String numToWall(int num, int n) {
		String ret = "";
		String binStr = Integer.toBinaryString(num);
		System.out.println(ret);
		if(binStr.length()<n) {
			for(int i=0; i<n-binStr.length(); i++) ret+=" ";
		}
		for(int i=0; i<binStr.length(); i++) {
			if(binStr.charAt(i)=='1') ret+="#";
			else ret+=" ";
		}
		System.out.println(ret);
		return ret;
	}
} 


```

