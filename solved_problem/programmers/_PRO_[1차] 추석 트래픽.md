# PRO_[1차] 추석 트래픽


```java


import java.util.*;
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.text.ParseException;
import java.text.SimpleDateFormat;

public class Practice {
	
	public static void main(String[] args) throws NumberFormatException, IOException, ParseException {
		Practice main = new Practice();
		String[] input1 = {"2016-09-15 01:00:04.001 2.0s",
				"2016-09-15 01:00:07.000 2s"};
		System.out.println(main.solution(input1));
	}
	
	static int[] start;
	static int[] end;
	
	public int solution(String[] lines) {
		int answer = 0;
		int length = lines.length;
		
		start = new int[length];
		end = new int[length];
        setTime(lines);
		
        int startTime = 0;
        int endTime = 0;
        
        for (int i=0; i<length; i++) {
            int count = 0;
        	startTime = start[i];
        	endTime = startTime + 1000 - 1;
        	
        	for(int j=0; j<length; j++) {
        		if(start[j] >= startTime && start[j] <= endTime) {
        			count++;
        		}
        		else if(end[j] >= startTime && end[j] <= endTime) {
        			count++;
        		}
        		else if(start[j] <= startTime && end[j] >= endTime) {
        			count++;
        		}
        	}

        	answer = Math.max(count, answer);
        }
        
        for (int i=0; i<length; i++) {
        	int count = 0;
        	startTime = end[i];
        	endTime = startTime + 1000 - 1;

        	for(int j=0; j<length; j++) {
        		if(start[j] >= startTime && start[j] <= endTime) {
        			count++;
        		}
        		else if(end[j] >= startTime && end[j] <= endTime) {
        			count++;
        		}
        		else if(start[j] <= startTime && end[j] >= endTime) {
        			count++;
        		}
        	}

        	answer = Math.max(count, answer);
        }
        
		return answer;
    }
	
	private void setTime(String[] lines) {
		for(int i=0; i<lines.length; i++) {
			String[] info = lines[i].split(" ");
			
			String[] time = info[1].split(":");
			String[] secTime = time[2].split("\\.");
			int secOfHour = Integer.parseInt(time[0]) * 60 * 60 * 1000;
			int secOfMin = Integer.parseInt(time[1]) * 60 * 1000;
			int sec = Integer.parseInt(secTime[0]) * 1000 + Integer.parseInt(secTime[1]);
			
			String[] responseTime = info[2].substring(0, info[2].length()-1).split("\\.");
			int diff = 0;
			
			if(responseTime.length == 1) {
				diff = Integer.parseInt(responseTime[0]) * 1000;
			} else {
				diff = Integer.parseInt(responseTime[0]) * 1000 + Integer.parseInt(responseTime[1]);
			}
			
			start[i] = secOfHour + secOfMin + sec - diff + 1;
			end[i] = start[i] + diff - 1;
		}
	}
}


```

