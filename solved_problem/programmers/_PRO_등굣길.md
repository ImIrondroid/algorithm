# PRO_등굣길


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		int[][] arr = {{2,2}};
		System.out.println(s.solution(4,3,arr));
	}

	public int solution(int m, int n, int[][] puddles) {
        int answer = 0;
        int[][] dp = new int[n][m];
        for(int i=0; i<puddles.length; i++) {
        	dp[puddles[i][0]-1][puddles[i][1]-1] = -1;
        }
        print(dp);
        return answer;
    }
	
	public void print(int[][] arr) {
		for(int i=0; i<arr.length; i++) {
			for(int j=0; j<arr[0].length; j++) {
				System.out.print(arr[i][j]+" ");
			}
			System.out.println();
		}
	}
}


```

