# PRO_가장 큰 정사각형 찾기


```java


import java.io.IOException;
import java.util.*;

class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		int[][] board = {{0,1,1,1},{1,1,1,1}};
		int[][] board1 = {{0,0,0,1},{0,0,0,0},{0,0,0,0},{0,0,0,0}};
		System.out.println(s.solution(board));
	}

	public int solution(int [][]board) {
		
		int answer = 0;
		int max = Integer.MIN_VALUE;
		
        int col = board.length;
        int row = board[0].length;
        
        for(int i=1; i<col; i++) {
        	for(int j=1; j<row; j++) {
        		int min = Math.min(board[i-1][j-1], Math.min(board[i][j-1], board[i-1][j]));
        		board[i][j] = min + 1;
        	}
        }
        //print(board);
        for(int i=0; i<col; i++) {
        	for(int j=0; j<row; j++) {
        		max = Math.max(max, board[i][j]);
        	}
        }
        
        answer = max*max;
        
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


	//시간초과
	public int solution1(int [][]board) {
		
        int answer = 0;
        int count = 0;
        int col = board.length;
        int row = board[0].length;
        
        for(int i=0; i<col; i++) {
        	for(int j=0; j<row; j++) {
        		if(board[i][j]==1) count++;
        	}
        }
        
        int limit = (int) Math.sqrt((double) count);
        
        Loop : for(int k=limit-1; k>=0 ;k--) {
        	for(int i=0; i<col-k; i++) {
            	for(int j=0; j<row-k; j++) {
            		if(check(board, i, j, k+1)) {
            			answer = (k+1)*(k+1);
            			break Loop;
            		}
            	}
            }
        }
        return answer;
    }
	
	public boolean check(int[][] board, int startX, int startY, int end) {
		for(int i=startX; i<startX+end; i++) {
			for(int j=startY; j<startY+end; j++) {
				if(board[i][j]!=1) return false;
			}
		}
		return true;
	}
}


```

