# PRO_탑


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();
		int[] arr = {6,9,5,7,4};
		System.out.println(solution.solution(arr));
	}
	 
	public int[] solution(int[] heights) {
	 
		int[] answer = new int[heights.length];
	
		for(int i=heights.length-1; i>=0; i--) {
			for(int j=i-1; j>=0; j--) {
				if(heights[i]<heights[j]) {
					answer[i] = j+1;
					break;
				}
			}
		}
		for(int i=0; i<heights.length; i++) {
			System.out.print(answer[i]+" ");
		}
		
		return answer;
	}
} 


```

