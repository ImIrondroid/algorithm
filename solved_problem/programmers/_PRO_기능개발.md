# PRO_기능 개발


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();
		int[] arr1 = {93,39,55};
		int[] arr2 = {1,30,5};
		System.out.println(solution.solution(arr1,arr2));
	}
	
	public int[] solution(int[] progresses, int[] speeds) {

		ArrayList<Integer> list = new ArrayList<>();
		Queue<Integer> queue = new LinkedList<Integer>();

		for(int i=0; i<progresses.length; i++) {
			queue.add(progresses[i]);
		}
		
		int count = 0;
		int index = 0;
		while(!queue.isEmpty()) {

			for(int i=index; i<progresses.length; i++) {
				progresses[i]+=speeds[i];
			}
			boolean flag = false;
			for(int i=index; i<progresses.length; i++) {
				if(progresses[i]>=100) {
					index++; count++; flag = true;
				} else break;
			}
			if(flag) {
				for(int i=0; i<count; i++) {
					queue.poll();	
					flag = false;
				}
				list.add(count);
			}
			count = 0;
		}
		
		int[] answer = new int[list.size()];
	        
	    for(int i=0; i<list.size(); i++) {
	       	answer[i] = list.get(i);
	       	System.out.print(answer[i]+ " ");
	    }
	        
	    return answer;
	}
} 


```

