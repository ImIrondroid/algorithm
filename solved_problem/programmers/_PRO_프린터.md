# PRO_프린터


```java


import java.io.IOException;
import java.util.*;

class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		System.out.println(s.solution(new int[] {1,1,9,1,1,1}, 0));
	}
	
	public int solution(int[] priorities, int location) {

		int max = Integer.MIN_VALUE;
		Queue<Point> queue = new LinkedList<>();
		Queue<Point> result = new LinkedList<Point>();
		
		boolean[] visit = new boolean[priorities.length];
		for(int i=0; i<priorities.length; i++) {
			queue.add(new Point(i, priorities[i]));
		}
		
		while(true) {
			int compare = getMaxPriority(priorities, visit);
			while(true) {
				Point front = queue.poll();
				if(front.priority == compare) {
					result.add(front);
					break;
				} else {
					queue.add(front);
				}
			}
			if(result.size()==priorities.length) break;
		}

        int answer = 0;
		while(!result.isEmpty()) {
			Point front = result.poll();
			if(front.index == location) {
				answer++;
				break;
			} else {
				answer++;
			}
		}
		
        return answer;
    }
	
	public int getMaxPriority(int[] priorities, boolean[] visit) {
		int max = Integer.MIN_VALUE;
		int index = 0;
		for(int i=0; i<visit.length; i++) {
			if(!visit[i] && max < priorities[i]) {
				max = priorities[i];
				index = i;
			}
		}
		visit[index] = true;
		return max;
	}
}

class Point{
	int index;
	int priority;
	Point(int index, int priority) {
		this.index = index;
		this.priority = priority;
	}
}


```

