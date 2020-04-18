# PRO_행렬의 곱셈


```java


import java.io.IOException;
import java.util.*;

class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		int[][] arr1 = {{2,3,2},{4,2,4},{3,1,4},{1,2,3}};
		int[][] arr2 = {{5,4,3,1,1},{2,4,1,2,1},{1,2,3,4,5}};
		System.out.println(s.solution(arr1, arr2));
	}
	
	
	public int[][] solution(int[][] arr1, int[][] arr2) {
		int col = arr1.length;
		int mid = arr1[0].length;
		int row = arr2[0].length;
        int[][] answer = new int[col][row];
        
        for(int i=0; i<col; i++) {
        	for(int j=0; j<row; j++) {
            	int sum = 0;
        		for(int m=0; m<mid; m++) {
        			sum += arr1[i][m] * arr2[m][j];
        		}
        		answer[i][j] = sum;
        	}
        }
        print(answer);
        return answer;
    }
	
	public void print(int[][] answer) {
		for(int i=0; i<answer.length; i++) {
			for(int j=0; j<answer[0].length; j++) {
				System.out.print(answer[i][j]+" ");
			}
			System.out.println();
		}
	}
}


```

