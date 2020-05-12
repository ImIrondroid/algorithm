# PRO_땅따먹기


//DP


```java


import java.util.*;


import java.io.IOException;
import java.util.*;

class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		int[][] board = {{1,2,3,5},{5,6,7,8},{4,3,2,1}};
		System.out.println(s.solution(board));
	}

	int solution(int[][] land) {
        int answer = Integer.MIN_VALUE;
        
        int[][] dp = new int[land.length][4];
        for(int i=0; i<4; i++) dp[0][i] = land[0][i];
        for(int i=1; i<dp.length; i++) {
        	
        	for(int m=0; m<4; m++) {
            	int max = Integer.MIN_VALUE;
        		for(int n=0; n<4; n++) {
        			if(m==n) continue;
        			else {
        				max = Math.max(max, dp[i-1][n]);
        			}
        		}
        		dp[i][m] = land[i][m] + max;
        	}
        }
        
        //print(dp);
       
        for(int i=0; i<4; i++) answer = Math.max(answer, dp[land.length-1][i]);

        return answer;
    }
	
	public void print(int[][] dp) {
		for(int i=0; i<dp.length; i++) {
			for(int j=0; j<dp[0].length; j++) {
				System.out.print(dp[i][j]+" ");
			}
			System.out.println();
		}
	}
}


```

