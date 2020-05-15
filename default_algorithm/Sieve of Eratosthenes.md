# 소수 판별 알고리즘 - Sieve of Eratosthenes(에라토스테네스의 체)


### 설명


에라토스테네스의 체는 가장 대표적인 소수(Prime Number) 판별 알고리즘입니다.
소수란 '양의 약수를 두 개만 가지는 자연수'를 의미합니다.
에라토스테네스의 체는 소수를 대량으로 빠르고 정확하게 구하는 방법입니다.


### 과정


1) 배열을 생성하여 값을 초기화합니다.
2) 2부터 시작해서 특정 숫자의 배수에 해당하는 숫자들을 모두 지웁니다.


```java


import java.util.*;


public class Eratosthenes {
	
	 public static void main(String[] args) throws IOException {
	    	
	    System.out.println(isPrimeNumber(3));
	    System.out.println(isPrimeNumberWithSqrt(3));
	    isPrimeNumberWithEratosthenes();
	 }
	 
	 //숫자 하나에 대한 소수 판별 시간 복잡도 O(N)
	 static boolean isPrimeNumber(int x) {
		 for(int i=2; i<x; i++) {
			 if(x%i==0) return false;
		 }
		 return true;
	 }
	 
	 //숫자 하나에 대한 소수 판별 시간 복잡도 O(N^(1/2))
	 static boolean isPrimeNumberWithSqrt(int x) {
		 int end = (int) Math.sqrt(x);
		 for(int i=2; i<=end; i++) {
			 if(x%i==0) return false;
		 }
		 return true;
	 }
	 
	 static int num = 100000;
	 static int[] arr = new int[100001];
	 
	 //숫자 여러개에 대한 소수 판별 시간 복잡도 O(N^2)
	 static void isPrimeNumberWithEratosthenes() {
		 for(int i=2; i<=num; i++) {
			 arr[i] = i;
		 }
		 for(int i=2; i<=num; i++) {
			 //이미 지워진 숫자는 무시
			 if(arr[i]==0) continue;
			 for(int j=i*2; j<=num; j+=i) {
				 arr[j] = 0;
			 }
		 }
		 for(int i=2; i<=num; i++) {
			 //지워지지 않은 경우는 소수이다.
			 if(arr[i]!=0) System.out.println(arr[i]+" ");
		 }
	 }
}


```

