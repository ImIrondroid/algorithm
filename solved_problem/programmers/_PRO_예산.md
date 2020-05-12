# PRO_예산


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();
		int[] arr = {1,3,2,5,4};
		System.out.println(solution.solution(arr,3));
	}
	
	public int solution(int[] d, int budget) {
	    
		int answer = 0;
	   
		int[] sortarr = d;
		Arrays.sort(sortarr);
		
		for(int i=0; i<d.length; i++) {
			if(budget-sortarr[i]>0) {
				budget-=sortarr[i];
				answer++;
			} else break;
		}
		
		return answer;
	}
}


```

