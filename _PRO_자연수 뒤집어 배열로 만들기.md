# PRO_자연수 뒤집어 배열로 만들기


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();

		long n = 1234567899999L;
		System.out.println(solution.solution(n));
	}
	
	public int[] solution(long n) {
	     
		ArrayList<Long> list = new ArrayList<>();
		while(n>0) {
			list.add(n%10);
			n/=10;
		}
		
		int[] answer = new int[list.size()];
		for(int i=0; i<answer.length; i++) {
			answer[i] = list.get(i).intValue();
			System.out.print(answer[i]+" ");
		}
	   
		return answer;
	 
	}
}


```

