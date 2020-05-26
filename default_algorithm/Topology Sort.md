# 위상 정렬 - Topology Sort


### 정의 


'순서가 정해져있는 작업'을 차례로 수행해야 할 때 그 순서를 결정해주기 위해 사용하는 알고리즘 입니다.


### 특징


1) 위상 정렬은 여러 개의 답이 존재할 수 있습니다.
2) DAG(Directed Acyclic Graph : 방향 그래프인데 싸이클이 존재하지 않는 그래프)에만 적용이 가능합니다.
3) 그래프의 위상 정렬이 가능한지, 가능하다면 그 결과가 무엇인지 알려주는 특징이 있습니다.
4) 시간 복잡도는 O(V+E)입니다. 즉 정접의 갯수 + 간선의 갯수만큼 소요됩니다.


### 과정


1) 진입차수(수행을 위한 조건)가 0인 정점을 큐에 삽입합니다.
2) 큐에서 원소를 꺼내 연결된 모든 간선을 제거합니다.
3) 간선 제거 이후에 진입차수가 0이 된 정점을 큐에 삽입합니다.
4) 큐가 빌 때까지 2~3번 과정을 반복합니다. 모든 원소를 방문하기 전에 큐가 빈다면 사이클이 존재하는 것이고, 모든 원소를 방문했다면 큐에서 꺼낸 순서가 위상 정렬의 결과입니다.


### 주의할점


위상 정렬은 시작점이 존재해야 하는데 사이클 그래프에서는 시작점을 찾을 수가 없습니다.


### 구현


```java


import java.util.*;

public class TopologySort {
	
	static int n = 7;
	static int[] inDegree = new int[8];
	static List<ArrayList<Integer>> list = new ArrayList<ArrayList<Integer>>(8);
	
	public static void main(String[] args) {
		for(int i=0; i<8; i++) list.add(new ArrayList<Integer>());
		list.get(1).add(2);
		inDegree[2]++;
		list.get(1).add(5);
		inDegree[5]++;
		list.get(2).add(3);
		inDegree[3]++;
		list.get(3).add(4);
		inDegree[4]++;
		list.get(4).add(6);
		inDegree[6]++;
		list.get(5).add(6);
		inDegree[6]++;
		list.get(6).add(7);
		inDegree[7]++;
		//사이클 발생
		//list.get(6).add(3);
		//inDegree[3]++;
		topologySort();
	}
	
	static void topologySort() {
		int[] result = new int[8];
		Queue<Integer> q = new LinkedList<Integer>();
		//진입 차수가 0인 노드를 큐에 삽입합니다.
		for(int i=1; i<8; i++) {
			if(inDegree[i]==0) q.add(i);
		}
		//위상 정렬이 완전히 수행되려면 정확히 N개의 노드를 방문합니다.
		for(int i=0; i<7; i++) {
			//n개를 방문하기 전에 큐가 빈다면 사이클이 발생한 것 입니다.
			if(q.isEmpty()) {
				System.out.println("사이클 발생!");
				return;
			} else {
				int x = q.poll();
				result[i] = x;
				for(int j=0; j<list.get(x).size(); j++) {
					int y = list.get(x).get(j);
					//새롭게 진입차수가 0이 된 정점을 큐에 삽입합니다.
					//진입 차수가 0이 되지 않으면 싸이클이 발생한다는 의미이기 때문에 큐에 넣지않아 큐가 비게 될 것입니다.
 					if(--inDegree[y]==0) {
						q.add(y);
					}
				}
			}
		}
		for(int i=0; i<n; i++) System.out.print(result[i]+" ");
	}
}


```

