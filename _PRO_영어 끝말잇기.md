# PRO_영어 끝말잇기


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		String[] arr = {"hello","observe","effect","take","either","recognize","encourage","ensure",
				"establish","hang","gather","refer","reference","estimate","executive"};
		System.out.println(s.solution(5, arr));
	}
	
	public int[] solution(int n, String[] words) {
        int[] answer = new int[2];
        int count = 1;
        int cycle = 1;
        Map<String, Integer> hash = new HashMap<String, Integer>();
        hash.put(words[0], 1);
        for(int i=0; i<words.length-1; i++) {
        	count++;
        	char last = words[i].charAt(words[i].length()-1);
        	char first = words[i+1].charAt(0);
        	if(last==first) {
        		if(!hash.containsKey(words[i+1])) hash.put(words[i+1], 1);
        		else {
        			answer[0] = count;
        			answer[1] = cycle;
        			break;
        		}
        	} else {
        		answer[0] = count;
    			answer[1] = cycle;
    			break;
        	}
        	if(count==n) {
        		cycle++;
        		count = 0;
        		if(i==words.length-2) {
        			answer[0] = 0;
        			answer[1] = 0;
        		}
        	}
        }
        System.out.println(answer[0] + " "+answer[1]);
        return answer;
    }
}


```

