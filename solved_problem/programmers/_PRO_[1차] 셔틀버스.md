# PRO_[1차] 셔틀버스


```java


import java.util.*;
import java.io.IOException;


public class Solution {
	
	public static void main(String[] args) throws IOException {
		Solution s = new Solution();
		String[] timetable1 = {"08:00","08:01","08:02","08:03"};
		String[] timetable2 = {"09:10","09:09","08:00"};
		String[] timetable3 = {"09:00","09:00","09:00","09:00"};
		String[] timetable4 = {"00:01","00:01","00:01","00:01","00:01"};
		String[] timetable5 = {"23:59"};
		String[] timetable6 = {"23:59","23:59","23:59","23:59","23:59","23:59",
				"23:59","23:59","23:59","23:59","23:59","23:59",
				"23:59","23:59","23:59","23:59"};
		System.out.println(s.solution(10,60,45,timetable6));
	}

	static StringTokenizer st;

	//https://programmers.co.kr/learn/courses/30/lessons/17678
	public String solution(int n, int t, int m, String[] timetable) {
        String answer = "";
        Queue<Integer> queue = new PriorityQueue<Integer>();
        for(int i=0; i<timetable.length; i++) queue.add(getMins(timetable[i]));

        //운행 반복
        int bustime = 540-t;
        for(int i=1; i<=n; i++) {
        	bustime += t;
        	for(int j=1; j<=m; j++) {
        		if(i==n && j==m) {
            		if(queue.isEmpty() || queue.peek()>bustime) {
            			answer = getTime(bustime);
            		} else if(!queue.isEmpty()){
            			answer = getTime(queue.peek()-1);
            		}
            		break;
        		}
        		if(queue.peek()<=bustime) {
        			queue.poll();
        		}
        	}
        }
        
        return answer;
    }
	
	static public int getMins(String s) {
		st = new StringTokenizer(s, ":");
		int hour = Integer.parseInt(st.nextToken());
		int min = Integer.parseInt(st.nextToken());
		return hour*60 + min;
	}
	
	static public String getTime(int mins) {
		String time = "";
		int hour = mins/60;
		int min = mins%60;
		if(hour<10) time = "0"+hour+":";
		else time = hour+":";
		if(min<10) time += "0"+min;
		else time += min;
		return time;
	}
}


```

