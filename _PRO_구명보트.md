# PRO_구명보트


//그리디


```java


import java.io.IOException;
import java.util.*;

class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		System.out.println(s.solution(new int[] {70,50,80,50}, 100));
	}

    public int solution(int[] people, int limit) {
    	
    	boolean[] visit = new boolean[people.length];
        int answer = 0;
        int index = 0;
        int end = 0;
        
        Arrays.sort(people);
        
        for(int i=0; i<people.length; i++) {
        	if(index>=people.length-end-1) break;
        	if(people[index]+people[people.length-1-end] <=limit) {
        		visit[index] = true;
        		visit[people.length-end-1] = true;
        		answer++;;
        		end++;
        		index++;
        	} else {
        		visit[people.length-end-1] = true;
        		answer++;
        		end++;
        	}
        }
        
        for(int i=0; i<visit.length; i++) {
        	if(!visit[i]) answer++;
        }
        
        return answer;
    }
}


```

