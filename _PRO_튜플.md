# PRO_튜플


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();

		//https://programmers.co.kr/learn/courses/30/lessons/64065
		System.out.println(solution.solution("{{2},{2,1},{2,1,3},{2,1,3,4}}"));
	}
	
	public int[] solution(String s) {
		
		HashMap<String, Integer> hashMap = new HashMap<>();
		Queue<Character> store = new LinkedList<Character>();
		
		for(int i=0; i<s.length(); i++) {
			int code = s.charAt(i);
			if(code>='0'&&code<='9') {
				//숫자 만나면 일단 store에 저장
				store.add(((char)code));
			} else {
				String str = "";
				while(!store.isEmpty()) {
					str+=store.poll();
				}
				if(!str.equals("")) {
					if(hashMap.get(str)==null) hashMap.put(str, 0);
					else hashMap.replace(str, hashMap.get(str)+1);
				}
				
			}
		}
		
		ArrayList<Integer> numList = new ArrayList<>();
		ArrayList<Integer> valueList = new ArrayList<>();
		
		Iterator iterator = hashMap.keySet().iterator();
		while(iterator.hasNext()) {
			String key = (String) iterator.next();
			numList.add(Integer.valueOf(key));
			valueList.add(hashMap.get(key));
		}
		
		int temp = 0;
		
		for(int i=0; i<valueList.size()-1; i++) {
			for(int j=0; j<valueList.size()-i-1; j++) {
				if(valueList.get(j)<valueList.get(j+1)) {
					temp = valueList.get(j+1);
					valueList.set(j+1, valueList.get(j));
					valueList.set(j, temp);
					temp = numList.get(j+1);
					numList.set(j+1, numList.get(j));
					numList.set(j, temp);
				}
			}
		}
		
		int[] answer = new int[numList.size()];
		for(int i=0; i<answer.length; i++) {
			answer[i] = numList.get(i);
		}
        return answer;
    }
}


```

