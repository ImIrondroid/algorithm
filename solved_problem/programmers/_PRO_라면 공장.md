# PRO_라면공장


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();
		int[] dates = {4,10,15};
		int[] supplies = {20,5,10};
		System.out.println(solution.solution(4, dates, supplies, 30));
	}
	
	public int solution(int stock, int[] dates, int[] supplies, int k) {
		
		Queue<Integer> queue = new PriorityQueue<Integer>(Comparator.reverseOrder());
        int answer = 0;
        int index = 0;
        int sum = stock;

        for(int i=0; i<k; i++) {
        	if(index<dates.length && i==dates[index]) 
        		queue.add(supplies[index++]);
        	if(stock==0) {
        		stock+=queue.poll();
        		answer++;
        	}
        	
        	stock--;
        }
        
        return answer;
    }
} 


```

