# 다익스트라 알고리즘 - Dijkstra Algorithm


### 설명

1) 다익스트라 알고리즘은 다이나믹 프로그래밍을 활용한 대표적인 최단 경로 탐색 알고리즘입니다.
2) 다익스트라 알고리즘은 특정한 하나의 정점에서 다른 모든 정점으로 가는 최단 경로를 알려줍니다.
3) 음의 간선은 포함하지 않는데, 현실 세계에서는 음의 간선이 존재하지 않기 때문에 다익스트라 알고리즘은 현실 세계에 사용하기 매우 적합한 알고리즘 중 하나라고 할 수 있습니다.


### 특징

1) 최단 거리는 여러개의 최단 거리로 이루어져 있기 때문에 다이나믹 프로그래밍으로 해결합니다.
2) 다익스트라 알고리즘은 정렬을 사용하기 때문에 정렬 이후에 가장 적은 것을 선택하는 이유로 그리디 알고리즘으로 해결할 수도 있습니다.
3) 현재까지 알고 있던 최단 경로를 계속해서 갱신합니다.


### 과정

1) 출발 노드를 설정합니다.
2) 출발 노드를 기준으로 각 노드의 최소 비용을 저장합니다.
3) 방문하지 않은 노드 중에서 가장 비용이 적은 노드를 선택합니다.
4) 해당 노드를 거쳐서 특정한 노드로 가는 경우를 고려하여 최소 비용을 갱신합니다.
5) 위 과정에서 3~4번을 반복합니다.


### 구현1 : 시간복잡도 O(N^2)


```java


import java.util.*;
import java.io.IOException;
import java.util.Arrays;
import java.util.HashMap;
import java.util.Iterator;
import java.util.List;
import java.util.Map;

public class Solution {
	
	static int num = 6;
	static int INF = 10000000;
	static int[][] arr = {
			{0, 2, 5, 1, INF, INF},
			{2, 0, 3, 2, INF, INF},
			{5, 3, 0, 3, 1, 5},
			{1, 2, 3, 0, 1, INF},
			{INF, INF, 1, 1, 0, 2},
			{INF, INF, 5, INF, 2, 0}
	};
	static boolean[] visit = new boolean[6]; //방문한 노드
	static int[] dis = new int[6]; //최단 거리 저장 
	
	public static void main(String[] args) throws IOException {
		dijkstra(0);
		for(int i=0; i<num; i++) {
			System.out.print(dis[i]+" ");
		}
	}

	//방문하지 않은 정점중에 가장 최소 거리를 가지는 정점을 반환
	static int getSmallIndex() {
		int min = INF;
		int index = 0;
		for(int i=0; i<num; i++) {
			if(dis[i]<min && !visit[i]) {
				min = dis[i];
				index = i;
			}
		}
		return index;
	}
	
	//다익스트라를 수행하는 함수
	//선형탐색 시간 복잡도 O(N^2)
	//정점의 갯수가 많은데 간선은 적을때 치명적일 정도로 비효율적임
	static void dijkstra(int start) {
		for(int i=0; i<num; i++) {
			dis[i] = arr[start][i];
		}
		visit[start] = true;
		for(int i=0; i<num-2; i++) {
			//가장 적은 비용이 드는 노드를 가져옴
			//가장 적은 비용의 Index를 가져올 때 힙을 이용한다면 O(logN)으로 가능
			int current = getSmallIndex();
			visit[current] = true;
			//그 노드의 인접한 노드 검사
			for(int j=0; j<num; j++) {
				if(!visit[j]) {
					//그 노드까지의 최소비용 + 그 노드를 거쳐서 인접한 노드로 가는 비용이 작다면
					if(dis[current] + arr[current][j] < dis[j]) {
						dis[j] = dis[current] + arr[current][j];
					}
				}
			}
		}
	}
}


```


### 구현2 : 시간복잡도 O(N*logN )


```java


import java.util.*;
import java.io.IOException;

public class Solution {
	
	public static void main(String[] args) throws IOException {
		//기본적으로 연결되지 않은 경우 비용은 무한
		for(int i=1; i<=num; i++) dis[i] = INF;
		for(int i=0; i<7; i++) list.add(new ArrayList());
		list.get(1).add(new Node(2, 2));
		list.get(1).add(new Node(3, 5));
		list.get(1).add(new Node(4, 1));
		
		list.get(2).add(new Node(1, 2));
		list.get(2).add(new Node(3, 3));
		list.get(2).add(new Node(4, 2));
		
		list.get(3).add(new Node(1, 5));
		list.get(3).add(new Node(2, 3));
		list.get(3).add(new Node(4, 3));
		list.get(3).add(new Node(5, 1));
		list.get(3).add(new Node(6, 5));

		list.get(4).add(new Node(1, 1));
		list.get(4).add(new Node(2, 2));
		list.get(4).add(new Node(3, 3));
		list.get(4).add(new Node(5, 1));
		
		list.get(5).add(new Node(3, 1));
		list.get(5).add(new Node(4, 1));
		list.get(5).add(new Node(6, 2));

		list.get(6).add(new Node(3, 5));
		list.get(6).add(new Node(5, 2));
		
		//매개변수는 특정한 지점 
		dijkstra(2);
		
		//결과 출력
		for(int i=1; i<=num; i++) {
			System.out.print(dis[i]+" ");
		}
	}

	static int num = 6;
	static int INF = 10000000;
	
	static int[] dis = new int[7];
	static List<ArrayList<Node>> list = new ArrayList<ArrayList<Node>>();
	
	static void dijkstra(int start) {
		dis[start] = 0;
		Queue<Node> queue = new PriorityQueue<Node>();
		queue.add(new Node(start, 0));
		while(!queue.isEmpty()) {
			Node node = queue.poll();
			int current = node.point;
			int distance = node.dis;
			//최단 경우가 아닌 경우 스킵
			if(dis[current] < distance) continue;
			for(int i=0; i<list.get(current).size(); i++) {
				//선택된 노드의 인접 노드
				int next = list.get(current).get(i).point;
				//선택된 노드를 거쳐서 인접 노드로 가는 비용
				int nextDistance = distance + list.get(current).get(i).dis;
				if(nextDistance < dis[next]) {
					dis[next] = nextDistance;
					queue.add(new Node(next , nextDistance));
				}
			}
		}
	}
}

class Node implements Comparable<Node>{
	int point;
	int dis;
	Node(int point, int dis) {
		this.point = point;
		this.dis = dis;
	}
	@Override
	public int compareTo(Node o) {
		return this.dis-o.dis;
	}
}


```
