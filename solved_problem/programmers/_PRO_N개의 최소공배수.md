# PRO_N개의 최소공배수


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		System.out.println(s.solution(new int[] {2,6,8,14}));
	}

	 public int solution(int[] arr) {
	    int answer = 0;

	    int[] lcm = new int[arr.length];
	    for(int i=0; i<arr.length-1; i++) {
	    	if(i==0) lcm[i] = arr[i]*arr[i+1]/gcd(arr[i],arr[i+1]);
	    	else lcm[i] = lcm[i-1]*arr[i+1]/gcd(lcm[i-1],arr[i+1]);
	    }
	    answer = lcm[arr.length-2];
	    
	    return answer;
	 }
	 
	 public int gcd(int left, int right) {
		 if(left%right==0)
			 return right;
		 return gcd(right, left%right);
	 }
}


```

