# 크루스칼 알고리즘 - Kruskal Algorithm


### 과정

- 모든 간선들을 '거리(비용)'을 기준으로 오름차순으로 정렬을 수행하고, 아래의 알고리즘에 맞게 그래프를 연결하면 가장 적은 비용으로 모든 노드를 연결한 그래프인 '최소 비용 신장 트리'가 만들어진다.

1) 정렬된 순서에 맞게 그래프에 포함시킨다.
2) 포함시키기 전에 Cycle Table을 확인한다. Cycle Table을 만들어 이용해야만 한다는 의미이다(Based on Union Find).
3) Cycle을 형성하는 경우 간선을 포함하지 않는다. 


### 구현


```java


package algorithm;

import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class Kruskal {

	public static void main(String[] args) {
		int n = 7;
		int m = 11;
		List<Edge> list = new ArrayList<>();
		list.add(new Edge(1,7,12));
		list.add(new Edge(1,4,28));
		list.add(new Edge(1,5,17));
		list.add(new Edge(1,2,67));
		list.add(new Edge(2,4,24));
		list.add(new Edge(2,5,62));
		list.add(new Edge(3,5,20));
		list.add(new Edge(3,6,37));
		list.add(new Edge(4,7,13));
		list.add(new Edge(5,6,45));
		list.add(new Edge(5,7,73));
		
		//간선의 비용을 기준으로 오름차순 정렬
		Collections.sort(list);
		
		//각 정점이 포함된 그래프가 어디인지 저장
		int[] parent = new int[11];
		for(int i=1; i<=10; i++) parent[i] = i;
		
		int sum = 0;
		for(int i=0; i<list.size(); i++) {
			//사이클이 발생하지 않는 경우 그래프에 포함
			Edge edge = list.get(i);
			if(!findParent(parent, edge.node[0], edge.node[1])) {
				sum += edge.dis;
				unionParent(parent, edge.node[0], edge.node[1]);
			}
		}
		
		System.out.println(sum);
	}

	//부모 노드를 찾는 함수
	static int getParent(int[] parent, int x) {
		if(parent[x]==x) return x;
		return parent[x] = getParent(parent, parent[x]);
	}
	
	//두 부모 노드를 합치는 함수
	static void unionParent(int[] parent, int a, int b) {
		a = getParent(parent, a);
		b = getParent(parent, b);
		if(a<b) parent[b] = a;
		else parent[a] = b;
	}
	
	//같은 부모를 가지는지 확인하는 함수
	static boolean findParent(int parent[], int a, int b) {
		a = getParent(parent, a);
		b = getParent(parent, b);
		if(a==b) return true; //서로 같은 부모, 같은 그래프 
		return false; //서로 다른 부모, 다른 그래프
	}
}

//간선 클래스 선언
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
		return this.dis-o.dis;
	}
}


```

