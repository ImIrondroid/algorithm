# PRO_같은 숫자는 싫어


```java


import java.awt.List;
import java.lang.reflect.Array;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.HashMap;
import java.util.Iterator;
import java.util.LinkedHashMap;

public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();
		int[] arr = {1,1,3,3,0,1,2,2,3};
		System.out.println(solution.solution(arr));
	}
	
	public int[] solution(int []arr) {
		
		ArrayList<Integer> list = new ArrayList<>();
		
		int start = 0;
		boolean isAdded = false;
		
		for(int i=0; i<arr.length-1; i++) {
			int init = arr[i];
			
			if(!isAdded) {
				list.add(init);
				isAdded = true;
			} 
			if(arr[i]==arr[i+1]) {
				continue;
			} else {
				isAdded = false;
			}
		}
		
		if(arr[arr.length-2]!=arr[arr.length-1]) {
			list.add(arr[arr.length-1]);
		}
		
        int[] answer = new int[list.size()];
        
        for(int i=0; i<list.size(); i++) {
        	answer[i] = list.get(i);
        }
        
        return answer;
	}
}


```

