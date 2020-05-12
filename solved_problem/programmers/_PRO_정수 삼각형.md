# PRO_정수 삼각형


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		int[][] arr = {{7},{3,8},{8,1,0},{2,7,4,4},{4,5,2,6,5}};
		System.out.println(s.solution(arr));
	}

	public int solution(int[][] triangle) {
        int answer = 0;
        int[][] dp = new int[500][500];
        
        dp[0][0] = triangle[0][0];
        
        for(int i=1; i<triangle.length; i++) {
        	for(int j=0; j<triangle[i].length; j++) {
        		if(j==0) {
            		dp[i][j] = triangle[i][j] + dp[i-1][j];
        		} else if(j==triangle[i].length-1) {
        			dp[i][j] = triangle[i][j] + dp[i-1][j-1];
        		} else {
        			dp[i][j] = triangle[i][j] + Math.max(dp[i-1][j], dp[i-1][j-1]);
        		}
        	}
        }
        
        int lastIdx = triangle.length-1;
        for(int i=0; i<triangle[lastIdx].length; i++) {
        	answer = Math.max(answer, dp[lastIdx][i]);
        }
        
        return answer;
    }
}


```

