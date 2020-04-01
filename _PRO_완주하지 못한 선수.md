# PRO_완주하지 못한 선수


```java


import java.util.Arrays;
import java.util.HashMap;
import java.util.Iterator;

public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		String[] participant = {"mislav","stanko","mislav","ana"};
		String[] completion = {"ana","stanko","mislav"};
		System.out.println(solution(participant, completion));
	}
	
	static public String solution(String[] participant, String[] completion) {
        
		String answer = "";
		HashMap<String, Integer> hashMap = new HashMap<>();
		
		for(int i=0; i<participant.length; i++) {
			String name = participant[i];
			if(hashMap.get(name)==null) hashMap.put(name, 1);
			else hashMap.put(name, hashMap.get(name)+1);
		}
		
		int index = 0;
		
		while(index!=completion.length) {
			String name = completion[index];
			if(hashMap.get(name)!=null) {
				if(hashMap.get(name)>1) {
					hashMap.replace(name, hashMap.get(name)-1);
				} else {
					hashMap.remove(name);
				}
			}
			index++;
		}
		
		Iterator iterator = hashMap.keySet().iterator();
		
		if(hashMap.size()==0) {
			answer = "";
		} else {
			answer = iterator.next().toString();
		}
		
        return answer;
    }
}


```

