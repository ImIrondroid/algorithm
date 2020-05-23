# 퀵 정렬 - QuickSort


### 아이디어


'특정한 값을 기준으로 큰 숫자와 작은 숫자를 나누면 어떨까?'


### 특징


1. 시간 복잡도가 O(nlogn)으로 비분할 정렬 알고리즘과 비교해 보았을때 빠르다.
2. 정렬된 리스트에서는 퀵 정렬의 불균등 분할의 수행시간이 더 많이 걸린다. 최악일때 시간복잡도가 N^2이다.
3. '분할 정복' 알고리즘중에 하나이다.
4. Merge Sort에 비교해 보았을때 pivot값을 이용하기 때문에 비균등하게 분할한다.


### 과정


1. 리스트 안의 한 요소를 먼저 선택하고 그 값을 pivot이라 칭한다.
2. low와 high값을 각각 pivot바로 오른쪽 값, 리스트의 맨오른쪽 값으로 이용한다.
3. low는 리스트의 마지막 값, high는 piovt값 다음의 값을 향하여 이동한다. 예시에서는 ++, --로 표현한다.
4. low와 high가 이동중에 pivot이 위치한 리스트 값과 각각의 index의 리스트 값을 계속하여 비교해 나간다.
5. low인덱스의 리스트 값이 high인덱스의 리스트 값보다 크면 swap을 시킨다.
6. 위의 과정들이 low가 high 값보다 작을때 계속하여 움직이면서 비교한다.


```java


import java.util.*;


public class QuickSort {
	
	static int num = 10;
	static int[] arr = {1,10,5,8,7,6,4,9,2,3};
	
	public static void main(String[] args) {
		quickSort(0,num-1);
		for(int i=0; i<arr.length; i++) {
			System.out.print(arr[i]+" ");
		}
	}
	
	static void quickSort(int start, int end) {
		if(start>=end) {
			//원소가 1개인 경우
			return;
		}
		
		int pivot = start; //pivot은 첫 번째 원소
		int low = start+1;
		int high = end; 
		int temp = 0;
		
		//엇갈릴 때까지 반복
		while(low<=high) {
			while(low<=end && arr[low]<=arr[pivot]) {
				//pivot 값보다 큰 값을 만날 때 까지 반복
				low++;
			}
			while(high>start && arr[high]>=arr[pivot]) {
				//pivot 값보다 작은 값을 만날 때 까지 반복
				high--;
			}
			if(low>high) {
				//현재 엇갈린 상태면 pivot 값과 교체
				temp = arr[high];
				arr[high] = arr[pivot];
				arr[pivot] = temp;
			} else {
				//엇갈린게 아니라면
				temp = arr[high];
				arr[high] = arr[low];
				arr[low] = temp;
			}
		}
		
		quickSort(start, high-1);
		quickSort(high+1, end);
	}
}


```

