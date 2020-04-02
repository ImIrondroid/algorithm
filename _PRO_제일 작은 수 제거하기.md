# PRO_제일 작은 수 제거하기


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();

		int[] arr = {4,3,2,1};
		System.out.println("    "+solution.solution(arr));
	}
	
	public int[] solution(int[] arr) {

		int[] subarr = arr;
		int[] answer = {};
		
		if(arr.length>1) {
			int index = 0;
			int min = subarr[0];
			for(int i=0; i<subarr.length; i++) {
				if(subarr[index]>subarr[i]) {
					index = i;
					min = subarr[i];
				}
			}
			
			ArrayList<Integer> list = new ArrayList<>();
			
			for(int i=0; i<subarr.length; i++) {
				if(subarr[i]!=min) {
					list.add(subarr[i]);
				}
			}
			if(list.size()>0) {
				answer = new int[list.size()];
				for(int i=0; i<list.size(); i++) {
					answer[i] = list.get(i);
				}
				return answer;
			} else {
				return new int[] {-1};
			}
		} else {
			return new int[] {-1};
		}
	}
}


```

