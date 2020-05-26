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


public class UnionFind {

	public static void main(String[] args) {

		int[] parent = new int[11];
		//우선 기본적으로 자기자신을 부모로 가리키게 만든다. Cycle Table을 만드는 과정
		for(int i=1; i<=10; i++) parent[i] = i;
		
		//첫 번째 그래프 집합
		unionParent(parent, 1, 2);
		unionParent(parent, 2, 3);
		unionParent(parent, 3, 4);
		//두 번째 그래프 집합
		unionParent(parent, 5, 6);
		unionParent(parent, 7, 6);
		unionParent(parent, 7, 8); 
		
		System.out.println("1과 5는 연결되어 있나요? : "+findParent(parent, 1,5));
		unionParent(parent, 1, 5);
		System.out.println("1과 5는 연결되어 있나요? : "+findParent(parent, 1,5));
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


```

