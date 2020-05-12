# PRO_섬 연결하기


```java


import java.util.*;
import java.io.IOException;
import java.util.Arrays;
import java.util.HashMap;
import java.util.Iterator;
import java.util.List;
import java.util.Map;

public class Solution {
	
	 public static void main(String[] args) throws IOException {
	    	
	    Solution s = new Solution();

	    int[][] costs = {{0,1,1},{0,2,2},{1,2,5},{1,3,1},{2,3,8}};
	    System.out.println(s.solution(4, costs));
	    
	 }
	
	 public int solution(int n, int[][] costs) {
		 int answer = 0;
	     List<Edge> list = new ArrayList<Edge>();
	     for(int i=0; i<costs.length; i++) {
	    	 int[] cost = costs[i];
	    	 list.add(new Edge(cost[0], cost[1], cost[2]));
	     }
	     Collections.sort(list);
	     
	     //사이클 테이블 만들기
	     int[] parent = new int[n];
	     for(int i=0; i<parent.length; i++) parent[i] = i;
	     
	     for(int i=0; i<list.size(); i++) {
	    	 Edge edge = list.get(i);
	    	 if(!findParent(parent, edge.node[0], edge.node[1])) {
	    		 answer += edge.dis;
	    		 unionParent(parent, edge.node[0], edge.node[1]);
	    	 }
	     }
	     
		 return answer;
	 }
	 
	 //부모 노드를 찾는 함수
	 static int getParent(int[] parent, int x) {
		 if(parent[x] == x) return x;
		 return parent[x] = getParent(parent, parent[x]);
	 }
	 
	 //두 부모 노드를 합치는 함수
	 static void unionParent(int[] parent, int a, int b) {
		 a = getParent(parent, a);
		 b = getParent(parent, b);
		 if(a>b) parent[a] = b;
		 else parent[b] = a;
	 }
	 
	 //같은 부모를 가지는지 확인하는 함수
	 static boolean findParent(int[] parent, int a, int b) {
		 a = getParent(parent, a);
		 b = getParent(parent, b);
		 if(a==b) return true;
		 return false;
	 }
}

class Edge implements Comparable<Edge>{
	int[] node;
	int dis;
	Edge(int a, int b, int dis) {
		node = new int[2];
		this.node[0] = a;
		this.node[1] = b;
		this.dis = dis;
	}
	@Override
	public int compareTo(Edge o) {
		return this.dis - o.dis;
	}
}


```

