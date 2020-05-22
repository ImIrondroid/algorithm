# 너비 우선 탐색 - Breath First Search


### 정의


탐색할 때 너비를 우선으로 하여 탐색을 수행하는 탐색 알고리즘입니다.


### 특징


1) '맹목적인 탐색'을 하고자 할 때 사용할 수 있는 탐색 기법입니다.
2) '최단 경로'를 찾아준다는 점에서 최단 길이를 보장해야 할 때 많이 사용합니다.
3) 큐(Queue)를 사용합니다.
4) 시작 노드(Start Node)를 큐에 삽입하면서 시작합니다.


### 과정

1) 큐에서 하나의 노드를 꺼냅니다.
2) 해당 노드의 연결된 노드 중 방문하지 않은 노드를 방문하고, 차례대로 큐에 삽입합니다.


### 구현


```java


import java.util.*;

public class Bfs {
	
	static int num = 8;
	static boolean[] visit = new boolean[8];
	static List<ArrayList<Integer>> list = new ArrayList<ArrayList<Integer>>();
	
	public static void main(String[] args) {
		for(int i=0; i<=7; i++) list.add(new ArrayList<Integer>());
		list.get(1).add(2);
		list.get(2).add(1);
		
		list.get(1).add(3);
		list.get(3).add(1);
		
		list.get(2).add(3);
		list.get(3).add(2);
		
		list.get(2).add(4);
		list.get(4).add(2);
		
		list.get(2).add(5);
		list.get(5).add(2);
		
		list.get(4).add(5);
		list.get(5).add(4);
		
		list.get(3).add(6);
		list.get(6).add(3);
		
		list.get(3).add(7);
		list.get(7).add(3);
		
		list.get(6).add(7);
		list.get(7).add(6);
		
		//bfs 수행
		bfs(1);
	}
	
	static void bfs(int start) {
		Queue<Integer> queue = new LinkedList<Integer>();
		queue.add(start);
		System.out.print(start+" ");
		visit[start] = true;
		while(!queue.isEmpty()) {
			int x = queue.poll();
			for(int i=0; i<list.get(x).size(); i++) {
				int y = list.get(x).get(i);
				if(!visit[y]) {
					queue.add(y);
					System.out.print(y+" ");
					visit[y] = true;
				}
			}
		}
	}
}


```

