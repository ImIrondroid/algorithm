# PRO_배달


```java


import java.io.IOException;
import java.util.*;

class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		int[][] arr = {{1,2,1},{1,3,2},{2,3,2},{3,4,3},{3,5,2},{3,5,3},{5,6,1}};
		System.out.println(s.solution(6,arr,4));
	}

	static int[] arr;
	static boolean[] visit;
	
	public int solution(int N, int[][] road, int K) {
        int answer = 0;

        List<ArrayList<Point>> list = new ArrayList<ArrayList<Point>>();
        visit = new boolean[N];
        arr = new int[N];
        
        for(int i=0; i<N; i++) {
        	visit[i] = false;
        	arr[i] = Integer.MAX_VALUE;
        }
        
        for(int i=0; i<N; i++) list.add(new ArrayList<Point>());
        for(int i=0; i<road.length; i++) {
        	int[] info = road[i];
        	list.get(info[0]-1).add(new Point(info[1]-1, info[2]));
        	list.get(info[1]-1).add(new Point(info[0]-1, info[2]));
        }
        
        dfs(list,0, 0, K);
        
        for(int i=0; i<visit.length; i++) if(visit[i]) answer++;
        
        return answer;
    }
	
	static void dfs(List<ArrayList<Point>> list, int prev, int sum, int target) {
		
		if(sum > target) {
			return;
		}
		
		visit[prev] = true;
		
		for(int i=0; i<list.get(prev).size(); i++) {
			Point p = list.get(prev).get(i);
			if(!visit[p.num] || sum+p.dis < arr[p.num]) {
				arr[p.num] = sum+p.dis;
				//System.out.println("prev : "+ prev+" "+"next : "+p.num+" -> "+(sum+p.dis));
				dfs(list, p.num, sum + p.dis, target);
			}
		}
	}
}

class Point {
	int num;
	int dis;
	Point(int num, int dis) {
		this.num = num;
		this.dis = dis;
	}
}


```

