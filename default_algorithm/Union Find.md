# Union Find Algorithm

Union Find란 Disjoint Set(서로소 집합 자료구조)을 표현할 때 사용하는 알고리즘이다.
여기서 Disjoint Set은 서로 중복되지 않는 부분 집합들로 나누어진 원소들에 대한 정보를 저장하고 조작하는 자료구조를 나타낸다.

Union-Find의 연산은 아래 3가지로 나누어진다.
1. Make-Set(x) : x를 유일한 원소로 하는 새로운 집합을 만든다.
2. Union(x, y) : x가 속한 집합과 y가 속한 집합을 합친다. 즉, x와 y가 속한 두 집합을 합치는 연산
3. Find(x) : x가 속한 집합의 대표값(루트 노드 값)을 반환한다. 즉, x가 어떤 집합에 속해 있는지 찾는 연산


```java


public class UnionFind {

	public static void main(String[] args) {

		int[] parent = new int[11];
		//우선 기본적으로 자기자신을 부모로 가리키게 만든다. Cycle Table을 만드는 과정
		for(int i=1; i<=10; i++) parent[i] = i;
		
		//첫 번째 그래프 집함
		unionParent(parent, 1, 2);
		unionParent(parent, 2, 3);
		unionParent(parent, 3, 4);
		//두 번째 그래프 집함
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

