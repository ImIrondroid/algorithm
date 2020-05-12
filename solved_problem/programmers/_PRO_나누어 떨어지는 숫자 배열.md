# PRO_나누어 떨어지는 숫자 배열


```java


import java.util.*;

public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();
		int arr[] = {5,9,7,10};
		System.out.println(solution.solution(arr,5));
	}
	
	public int[] solution(int[] arr, int divisor) {
	
		ArrayList<Integer> list = new ArrayList<>();
		for(int i=0; i<arr.length; i++) {
			if(arr[i]%divisor==0) list.add(arr[i]);
		}
		
		if(list.size()>0) {
			int[] answer = new int[list.size()];
			
			Collections.sort(list);
			for(int i=0; i<list.size(); i++) {
				answer[i] = list.get(i);
			}
			return answer;
		} else {
			return new int[] {-1};
		}
		
	}
}


```

