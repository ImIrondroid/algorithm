# PRO_방문 길이


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		System.out.println(s.solution("ULURRDLLU"));
	}

	static int[] dx = {0, 0, 1, -1};
	static int[] dy = {-1, 1, 0, 0};
	
	public int solution(String dirs) {
        int answer = 0;
        int startX = 0;
        int startY = 0;
        
        Map<String, Integer> hash = new HashMap<String, Integer>();
        for(int i=0; i<dirs.length(); i++) {
        	char c = dirs.charAt(i);
        	
        	String order = startX+","+startY+"->";
        	String reverse = startX+","+startY;
        	
        	int dir = 0;
        	switch(c) {
        	case 'U':
        		dir = 0;
        		break;
        	case 'D':
        		dir = 1;
        		break;
        	case 'R':
        		dir = 2;
        		break;
        	case 'L':
        		dir = 3;
        		break;
        	}
        	
        	startX+=dx[dir];
        	startY+=dy[dir];
        	
        	if(startX<-5 || startY<-5 || startX>5 || startY>5) {
            	startX-=dx[dir];
            	startY-=dy[dir];
        		continue;
        	}
        	
        	order += startX+","+startY;
        	reverse = startX+","+startY+"->"+reverse;
        	//System.out.println(order +"   "+reverse);
        	if(!hash.containsKey(order) && !hash.containsKey(reverse)) {
        		hash.put(order, 1);
        		hash.put(reverse, 1);
        		answer++;
        	}
        }
        return answer;
    }
}


```

