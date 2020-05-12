# PRO_[3차] 압축


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		System.out.println(s.solution("ABABABABABABABAB"));
	}
	
	public int[] solution(String msg) {  
	    Map<String, Integer> hashMap = new HashMap<>();
	    ArrayList<Integer> list = new ArrayList<>();
	    for(int i=0; i<=25; i++) hashMap.put(String.valueOf((char)((int)'A'+i)), i+1);
	    String temp = "";
	    for(int i=0; i<msg.length(); i++) {
	    	char now = msg.charAt(i);
	    	temp += String.valueOf(now);
	    	if(!hashMap.containsKey(temp)) {	
	    		list.add(hashMap.get(temp.substring(0, temp.length()-1)));
	    		hashMap.put(temp, hashMap.size()+1);
	    		temp = String.valueOf(now);
	    		
	    	} 
	    	if(i==msg.length()-1) {
    			list.add(hashMap.get(temp));
    		}
	    }

		int[] answer = new int[list.size()];
		for(int i=0; i<answer.length; i++) {
			answer[i] = list.get(i);
		}
		return answer;
	}
	
	public void print(ArrayList<Integer> list) {
		for(int i=0; i<list.size(); i++) System.out.print(list.get(i)+" ");
		System.out.println();
	}
}


```

