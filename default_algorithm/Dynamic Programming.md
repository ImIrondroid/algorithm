# 동적 계획법 - Dynamic Programming


### 정의


동적 계회법이란 '하나의 문제는 단 한 번만 풀도록 하는 알고리즘'입니다.
크고 어려운 문제를 작은 문제로 나누어 처리한 뒤에 전체의 답을 구하는 것입니다.


### 가정


1) 큰 문제를 작은 문제로 나눌 수 있습니다.
2) 작은 문제에서 구한 정답은 그것을 포함하는 큰 문제에서도 동일합니다.


### 특징


메모이제이션이 사용된다는 점에서 분할정복 알고리즘과 다릅니다.
이미 계산한 결과를 배열에 저장함으로써 나중에 동일한 계산을 피할수 있게 됩니다.


### 간단한 동적 계획법 구현 


```java


import java.util.*;


public class DynamicProgramming {

	static int[] d = new int[1001];
	
	public static void main(String[] args) {
		//연산 2^50번 수행
		//System.out.println(dp(50));
		System.out.println(memodp(1000));
	}
	
	//시간복잡도 O(2^N), 시간이 오래 걸림
	static int dp(int x) {
		if(x==1 || x==2) return 1;
		return dp(x-1) + dp(x-2);
	}
	
	//시간복잡도 O(N)
	static int memodp(int x) {
		if(x==1 || x==2) return 1;
		if(d[x]!=0) return d[x]; //이미 구했던 숫자라면 사용
		return d[x] = (memodp(x-1) + memodp(x-2))%10007; //오버플로우 발생 처리
	}
}


```

