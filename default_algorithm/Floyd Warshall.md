# 플로이드 와샬 알고리즘 - Floyd Warshall


### 개념

'모든 정점'에서 '모든 정점'으로의 최단 경로를 구하는 알고리즘 입니다.

### 특징

다익스트라 알고리즘은 가장 적은 비용을 하나씩 선택해야 했다면 플로이드 와샬 알고리즘은 기본적으로 '거쳐가는 정점'을 기준으로 알고리즘을 수행한다.
다익스트라 '1차원 배열', 플로이드 와샬 '2차원 배열'을 사용하여 풀이한다.
동적 프로그래밍 기법을 그대로 사용하여 구현한다.


### 과정

2차원 배열을 만들고 그래프의 간선 정보를 저장한다. (* 두 정점의 직접적으로 연결이 없으면 무한대 값으로, 자기 자신으로의 거리는 0으로 저장 한다.)
노드 1을 거쳐가는 경우를 가정하면, 2차원 배열중에서 index가 1인 경우를 제외하고 갱신하여 준다.
예시 - (2,3)를 갱신해 줄때 비교해야 되는 상대값은 (2,1) + (1,3) 입니다.


```java


import java.util.*;


public class DynamicProgramming {

	static int num = 4;
	static int INF = 10000000;
	//테이블이 의미하는 바는 '현재까지 계산된 최소의 비용'입니다.
	static int[][] arr = {
			{0, 5, INF, 8},
			{7, 0, 9, INF},
			{2, INF, 0, 4},
			{INF, INF, 3, 0}
	};
	
	public static void main(String[] args) {
		floydWarshall();
	}
	
	static void floydWarshall() {
		//결과 그래프 초기화
		int[][] ret = new int[4][4];
		for(int i=0; i<num; i++) {
			for(int j=0; j<num; j++) {
				ret[i][j] = arr[i][j];
			}
		}
		
		//k는 거쳐가는 노드
		for(int k=0; k<num; k++) {
			//i는 출발 노드
			for(int i=0; i<num; i++) {
				//j는 도착 노드
				for(int j=0; j<num; j++) {
					if(ret[i][k] + ret[k][j] < ret[i][j]) {
						ret[i][j] = ret[i][k] + ret[k][j];
					}
				}
			}
		}
		
		for(int i=0; i<num; i++) {
			for(int j=0; j<num; j++) {
				System.out.print(ret[i][j]+" ");
			}
			System.out.println();
		}
	}
}


```

