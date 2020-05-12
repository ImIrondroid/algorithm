# SWEA_아바바바


```java


import java.util.*;
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
	

public class Main {
	
	public static void main(String args[]) throws Exception
	{
		Scanner sc = new Scanner(System.in);
		long T;
		T=sc.nextLong();
		
		for(int test_case = 1; test_case <= T; test_case++)	{
			long N = sc.nextLong()/2;
			System.out.println("#"+test_case+" "+N*N);
		}
	}
	
	//long 타입 반환에서 이 return 값은 옳지 못함.
	public static long decal(int N) {
		//abababababa
		//N == 3 aba 1 + 0
		//N == 5 aba, aba, ababa, bab 3 + 1
		//N == 7 aba, aba, aba, ababa, ababa, abababa, bab, bab, babab 6 + 3
		//N == 9 aba, aba, aba, aba, ababa, ababa, ababa, abababa, abababa, ababababa
		//		 bab, bab, bab, babab, babab, bababab
		//N == 11 aba, aba, aba, aba, aba, ababa, ababa, ababa, ababa, abababa, abababa, abababa, ababababab
		//aba -> 1, 3, 6, 10, 15  dn -> n(n+1)/2;
		//bab -> 0, 1, 3, 6, 10   dn -> n(n-1)/2;
		//+   -> 1, 4, 9, 16, 25  dn -> n^2;
		
		return (long) Math.pow(N, 2);
	}
}


```

