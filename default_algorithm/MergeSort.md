# 병합 정렬 - MergeSort


### 아이디어


'일단 반으로 나누고 나중에 합쳐서 정렬하면 어떨까?'


### 개념


1) '존 폰 노이만'이라는 사람이 제인한 알고리즘이다.
2) 분할, 정복, 결합의 단계로 이루어지는 알고리즘이다.
3) 분할 정복 방법중에 하나이다.
4) 일반적인 방법에서는 안정 정렬에 속한다.


### 특징


1) 안정적인 정렬 방법이고 시간 복잡도가 O(nlogn)으로 다른 정렬 알고리즘과 비교해 보았을때 가장 빠르편에 속한다.
2) 퀵 정렬과 다르게 최악일때도 시간복잡도가 O(nlogn)이다.
3) 큰 레코드를 정렬할 경우 어떤 정렬 방법보다 효율적이다.


### 과정


1) 우선 mergeSort()의 파라미터로 list와 ,첫번째 인덱스, 인덱스의 마지막 값을 넘겨주어 실행한다.
2) mid값을 기준으로 왼쪽과 오른쪽의 배열을 나누어 mergeSort를 계속해서 분리한다.
3) m과 n이 같을 때(데이터가 1개만 있을 때) merge()를 순차적으로 실행할 것 이다.
4) 정렬된 값은 sorted 배열에 정렬되어 저장되어 있기때문에 원래 arr 배열에 다시 저장해준다.


```java


import java.util.*;

public class MergeSort {
	
	static int num = 8;
	static int[] sorted = new int[8]; //정렬을 위해 사용되는 배열
	
	public static void main(String[] args) {
		int[] arr = {1,5,8,7,6,4,2,3};
		mergeSort(arr, 0, num-1);
		for(int i=0; i<num; i++) System.out.print(arr[i]+" ");
	}
	
	static void merge(int a[], int m, int mid, int n) {
		int i = m;
		int j = mid+1;
		int k = m;
		//작은 순서대로 배열에 삽입
		while(i<=mid && j<=n) {
			if(a[i]<=a[j]) {
				sorted[k++] = a[i++];
			} else {
				sorted[k++] = a[j++];
			}
		}
		//남은 데이터 삽입
		if(i>mid) {
			for(int t=j; t<=n; t++) {
				sorted[k++] = a[t];
			}
		} else {
			for(int t=i; t<=mid; t++) {
				sorted[k++] = a[t];
			}
		}
		
		//정렬된 배열 옮기기
		for(int t=m; t<=n; t++) {
			a[t] = sorted[t];
		}
	}
	
	static void mergeSort(int a[], int m, int n) {
		//크기가 1보다 큰 경우
		if(m<n) {
			int mid = (m+n)/2;
			mergeSort(a, m, mid);
			mergeSort(a, mid+1, n);
			merge(a,m,mid,n);
		}
	}
}


```

