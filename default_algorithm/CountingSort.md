# 계수 정렬 - CountingSort


### 아이디어


'크기를 기준으로 갯수를 세면 어떨까?'


### 특징


1) '범위 조건'이 있는 경우에 한해서 굉장히 빠른 알고리즘입니다.
3) 데이터의 크기가 한정되어 있을 때에만 사용가능한 알고리즘입니다.
2) 시간복잡도가 O(n)입니다.


```java


import java.util.*;

public class CountingSort {
	
	public static void main(String[] args) {
		int temp = 0;
		int[] count = new int[5];
		int[] arr = {
				1,3,2,4,3,2,5,3,1,2,
				3,4,4,3,5,1,2,3,5,2,
				3,1,4,3,5,1,2,1,1,1
		};
		for(int i=0; i<5; i++) {
			count[i] = 0;
		}
		for(int i=0; i<30; i++) {
			count[arr[i]-1]++;
		}
		for(int i=0; i<5; i++) {
			if(count[i]!=0) {
				for(int j=0; j<count[i]; j++) {
					System.out.print((i+1)+" ");
				}
			}
		}
	}
}


```