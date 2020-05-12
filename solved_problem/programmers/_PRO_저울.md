# PRO_저울


//그리디


```java


import java.util.*;
import java.io.IOException;
import java.util.Arrays;
import java.util.HashMap;
import java.util.Iterator;
import java.util.List;
import java.util.Map;

public class Solution {
	
	 public static void main(String[] args) throws IOException {
	    	
	    Solution s = new Solution();
	    int[] arr = {3, 1, 6, 2, 7, 30, 1};
	    int[] arr1 = {1,2};
	    System.out.println(s.solution(arr));
	    
	 }
	    
	 public int solution(int[] weight) {
		 int answer = 1;
		 Arrays.sort(weight);
		 for(int i=0; i<weight.length; i++) {
			 if(weight[i] > answer) break;
			 answer += weight[i];
		 }
		 return answer;
	 }
	 
	 //시간초과
	 public int solution1(int[] weight) {
		 int answer = 0;
	     int max = Integer.MIN_VALUE;
		 Arrays.sort(weight);
		 
		 List<Integer> copy = new ArrayList<>();
		 Map<Integer, Integer> hash = new HashMap<Integer,Integer>();
		 hash.put(weight[0], weight[0]);
		 
		 for(int i=1; i<weight.length; i++) {
			int w = weight[i];
			Iterator<Integer> it = hash.keySet().iterator();
			while(it.hasNext()) {
				int next = it.next();
				int sum = w + next;
				if(!hash.containsKey(sum)) {
					copy.add(w+next);
					max = Math.max(max, w+next);
				}
			}
			for(int j=0; j<copy.size(); j++) hash.putIfAbsent(copy.get(j), copy.get(j));
			copy.clear();
		 }
		 
		 for(int i=0; i<max; i++) {
			 if(hash.get(i+1)==null) {
				 answer = i+1;
				 break;
			 }
		 }
		 
		 return answer;
	 }
}



```

