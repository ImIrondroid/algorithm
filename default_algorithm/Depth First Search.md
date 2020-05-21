# 깊이 우선 탐색 - Depth First Search


### 정의


탐색을 함에 있어서 보다 깊은 것을 우선적으로 하여 탐색하는 알고리즘입니다.


### 특징


1) 너비 우선 탐색(Breadth First Search)에서 큐(Queue)가 사용된다면 깊이 우선 탐색에서는 스택(Stack)이 사용됩니다.
2) 스택을 사용하지 않아도 컴퓨터가 구조적으로 스택의 원리를 사용하기 때문에 직접 구현하지 않아도 사용이 가능합니다.


### 구현


```java


import java.util.*;

public class Dfs {
	
	static int num = 8;
	static boolean[] visit = new boolean[8];
	static List<ArrayList<Integer>> list = new ArrayList<ArrayList<Integer>>();
	
	public static void main(String[] args) {
		for(int i=0; i<8; i++) list.add(new ArrayList<Integer>());
		//정점 연결 시키기
		list.get(1).add(2);
		list.get(2).add(1);
		list.get(1).add(3);
		list.get(3).add(1);
		list.get(2).add(3);
		list.get(3).add(2);
		list.get(2).add(4);
		list.get(4).add(2);
		list.get(3).add(6);
		list.get(6).add(3);
		list.get(3).add(7);
		list.get(7).add(3);
		list.get(4).add(5);
		list.get(5).add(4);
		list.get(6).add(7);
		list.get(7).add(6);
		
		//DFS 수행
		dfs(1);
	}
	
	static void dfs(int x) {
		if(visit[x]) return;
		visit[x] = true;
		System.out.print(x+" ");
		for(int i=0; i<list.get(x).size(); i++) {
			int y = list.get(x).get(i);
			dfs(y);
		}
	}
}


```

