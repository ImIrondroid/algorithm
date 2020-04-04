# PRO_네트워크


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();
		int[][] arr = {{1,1,0},{1,1,0},{0,0,1}};
		System.out.println(solution.solution(3, arr));
	}
	
	public int solution(int n, int[][] computers) {
        int answer = 0;
        boolean[][] visit = new boolean[n][n];
        
        for(int i=0; i<n; i++) {
    		if(!visit[i][i]) {
    			dfs(computers, visit, i, n);
    			answer++;
    		}
    	}
        
        return answer;
    }
	
	public void dfs(int[][] computers, boolean[][] visit, int j, int n) {
		for(int i=0; i<n; i++) {
			if(computers[j][i]==1 && !visit[j][i]) {
				visit[j][i] = true;
				visit[i][j] = true;
				dfs(computers, visit, i, n);
			}
		}
	}
} 


```

