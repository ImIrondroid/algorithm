# PRO_등굣길


```java


import java.util.*;
import java.io.IOException;
import java.util.Arrays;
import java.util.HashMap;
import java.util.Iterator;
import java.util.List;
import java.util.Map;


public class Solution {
	
	 public static void main(String[] args) throws IOException {
	    	
	    Solution s = new Solution();
	    int[][] puddles = {{2,1}};
	    System.out.println(s.solution(3,3,puddles));   
	 }
	 
	 static int[][] map = new int[101][101];
	 public int solution(int m, int n, int[][] puddles) {
		
		//예외 무조건 경우의 수 1인 경우
		if(m==1 || n==1) return 1;
		
		//웅덩이 지점 1로 초기화
		for(int i=0; i<puddles.length; i++) map[puddles[i][1]][puddles[i][0]] = -1;
		
		//시작점을 제외한 첫 번째 col 1로 채우기
		boolean flag = false;
		for(int i=2; i<=m; i++) {
			if(map[1][i]!=-1) map[1][i] = 1;
			else if(map[1][i]==-1) flag = true;
			if(flag) break;
		}
		flag = false;	
		for(int i=2; i<=n; i++) {
			if(map[i][1]!=-1) map[i][1] = 1;
			else if(map[i][1]==-1) flag = true;
			if(flag) break;
		}
		for(int i=1; i<=n; i++) {
			for(int j=1; j<=m; j++) System.out.print(map[i][j]+" ");
			System.out.println();
		}
		
		for(int i=2; i<=n; i++) {
			for(int j=2; j<=m; j++) {
				if(map[i][j]==-1) {
					map[i][j] = 0;
					continue;
				}
				if(map[i][j-1]==-1 && map[i-1][j]!=-1) {
					map[i][j] = map[i-1][j];
				} else if(map[i][j-1]!=-1 && map[i-1][j]==-1) {
					map[i][j] = map[i][j-1]; 
				} else if(map[i][j-1]==-1 && map[i-1][j]==-1) {
					map[i][j] = 0;
				} else {
					map[i][j] = (map[i][j-1] + map[i-1][j])%1000000007;
				}
			}
		}
		
		for(int i=1; i<=n; i++) {
			for(int j=1; j<=m; j++) System.out.print(map[i][j]+" ");
			System.out.println();
		}
        return map[n][m];
    }
}


```

