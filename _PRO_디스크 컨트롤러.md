# PRO_디스크 컨트롤러


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		int[][] jobs = {{0,3},{1,9},{2,6}};
		System.out.println(s.solution(jobs));
	}

	public int solution(int[][] jobs) {
        Queue<Point> queue = new PriorityQueue<Point>();
        List<Point> list = new ArrayList<Point>();
        for(int[] item : jobs) queue.add(new Point(item[0], item[1]));
        while(!queue.isEmpty()) list.add(queue.poll());
        
        int time = 0;
        int answer = 0;
        while(!list.isEmpty()) {
        	Loop : for(int i=0; i<list.size(); i++) {
        		if(time>=list.get(i).requesttime) {
        			time += list.get(i).processtime;
        			answer += (time-list.get(i).requesttime);
        			list.remove(i);
        			break Loop;
        		}
        		if(i==list.size()-1) {
        			time++;
        		}
        	}
        }
        print(list);
        
        return answer/jobs.length;
    }
	
	static void print(List<Point> list) {
		for(int i=0; i<list.size(); i++) System.out.print(list.get(i)+" ");
		System.out.println();
	}
}

class Point implements Comparable<Point> {
	int requesttime;
	int processtime;
	Point(int requesttime, int processtime) {
		this.requesttime = requesttime;
		this.processtime = processtime;
	}
	 
	@Override
	public String toString() {
		// TODO Auto-generated method stub
		return "{"+requesttime+","+processtime+"}";
	}
	
	@Override
	public int compareTo(Point o) {
		return this.processtime==o.processtime? this.requesttime-o.requesttime : this.processtime-o.processtime;
	}
}


```

