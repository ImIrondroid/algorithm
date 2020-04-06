# SWEA_어디에 단어가 들어갈 수 있을까


```java


import java.util.*;


class Solution {
	public static void main(String args[]) throws Exception {
		
		Scanner sc = new Scanner(System.in);
		
		int T;
		
		T=sc.nextInt();
		
		for(int k=1; k<=T; k++) {
			
			int N = sc.nextInt();
			int K = sc.nextInt();
			int cnt = 0;
			
			int[][] map = new int[N][N];
			
			for(int i=0; i<N; i++) {
				for(int j=0; j<N; j++) {
					map[i][j] = sc.nextInt();
				}
			}
			
			for(int i=0; i<N; i++) {
				int colcount = 0;
				int rowcount = 0;
				
				for(int j=0; j<N; j++) {
					
					if(map[i][j]==1) {
						colcount++;
					}
					else {
						if(colcount==K) cnt++;
						colcount = 0;
					}
					if(map[j][i]==1) {
						rowcount++;
					}
					else {
						if(rowcount==K) cnt++;
						rowcount = 0;
					}
				}
				
				if(colcount==K) cnt++;
				if(rowcount==K) cnt++;
			}
			System.out.println("#"+k+" "+cnt);
		}
	}
}


```

