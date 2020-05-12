# SWEA_스도쿠 검증


```java


import java.util.*;


class Solution {
	
	public static void main(String args[]) throws Exception {
		
		Scanner sc = new Scanner(System.in);
		
		int T;
		
		T=sc.nextInt();
		
		for(int k=1; k<=T; k++) {
			
			int[][] map = new int[9][9];
			boolean flag = true;
			
			for(int i=0; i<9; i++) {
				for(int j=0; j<9; j++) {
					map[i][j] = sc.nextInt();
				}
			}
			
			for(int i=0; i<9; i++) {
				int colsum = 0;
				int rowsum = 0;
				for(int j=0; j<9; j++) {
					colsum += map[i][j];
					rowsum += map[j][i];
				}
				if(colsum!=45 || rowsum!=45) {
					flag = false;
					break;
				}
			}
			
			if(flag) {
				for(int i=0; i<3; i++) {
					int sum = 0;
					for(int m=i*3; m<i*3+3; m++) {
						for(int n=i*3; n<i*3+3; n++) {
							sum += map[m][n];
						}
					}
					if(sum!=45) {
						flag = false;
						break;
					}
				}
			}
			
			if(flag) System.out.println("#"+k+" "+1);
			else  System.out.println("#"+k+" "+0);
		}
	}
}


```

