# 힙 정렬 - HeapSort


### 개념


1) 완전 이진트리의 일종으로 우선순위 큐를 위하여 만들어진 자료구조이다.
2) 최댓값, 최솟값을 쉽게 추출할 수 있는 자료구조이다.
3) 힙 트리 구조(Heap Tree Structure)로 구성하여 정렬하는 방법
4) 최솟값이나 최댓값을 빠르게 찾아내기 위해 완전 이진 트리를 기반으로 하는 트리이다.


### 특징


1) 시간 복잡도가 O(nlogn)으로 다른 정렬 알고리즘과 비교해 보았을때 가장 빠르편에 속한다.
2) 퀵 정렬과 다르게 최악일때도 시간복잡도가 O(nlogn)이다.
3) 가장 큰 값이나 가장 작은 값을 찾을때 유용한 정렬이다.


```java


import java.util.*;

public class HeapSort {
	
	static int num = 8;
	static int[] heap = {7,6,5,4,3,2,1,8};
	
	public static void main(String[] args) {
		//전체 트리 구조를 최대 힙 구조로 바꾸기
		for(int i=1; i<num; i++) {
			int c = i;
			do {
				int root = (c-1)/2; //부모를 가리킴
				if(heap[root] < heap[c]) {
					int temp = heap[root];
					heap[root] = heap[c];
					heap[c] = temp;
				} 
				c = root;
			} while(c!=0);
		}
		//크기를 줄여가면서 반복적으로 힙을 구성
		for(int i=num-1; i>=0; i--) {
			int temp = heap[0];
			heap[0] = heap[i];
			heap[i] = temp;
			int root = 0;
			int c = 1;
			do {
				c = 2*root+1;
				//자식 중에 더 큰 값 찾기
				if(c<i-1 && heap[c]<heap[c+1]) {
					c++;
				}
				if(c<i && heap[root]<heap[c]) {
					temp = heap[root];
					heap[root] = heap[c];
					heap[c] = temp;
				}
				root = c;
			} while(c<i);
		}
		
		for(int i=0; i<num; i++) {
			System.out.print(heap[i]+" ");
		}
	}
}


```

