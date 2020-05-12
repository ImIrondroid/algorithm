# PRO_자물쇠와 열쇠


```java


import java.io.IOException;
import java.util.*;


class Solution {

	static int hole = 0;
	static int[] dx = {0,1,0,-1};
	static int[] dy = {1,0,-1,0};
	 
	static int[][] copymap;
	static int[][] copyedlock;
	static boolean[][] visit;
	 
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		int[][] key = {{0,0,0},{1,0,0},{0,1,1}};
		int[][] lock = {{1,1,1},{1,1,0},{1,0,1}};
		System.out.println(s.solution(key, lock));
	}

	 public boolean solution(int[][] key, int[][] lock) {
	      
		 boolean answer = true;
	     int keysize = key.length;
	     int locksize = lock.length;
	     visit = new boolean[keysize][keysize];
	     copymap = new int[keysize][keysize];
	     copyedlock = new int[locksize+2*(keysize-1)][locksize+2*(keysize-1)];
	     
	     for(int i=keysize-1; i<copyedlock.length-keysize+1; i++) {
	    	 for(int j=keysize-1; j<copyedlock.length-keysize+1; j++) 
	    		 copyedlock[i][j] = lock[i-keysize+1][j-keysize+1];
	     }
	     
	     for(int i=0; i<locksize; i++) {
	    	 for(int j=0; j<locksize; j++) {
	    		 if(lock[i][j]==0) hole++;
	    	 }
	     }
	     
	     answer = rotate(key, 8);
	     
		 return answer;
	 }
	 
	 
	 public static boolean rotate(int[][] map, int dis) {
		 
		 for(int cycle=0; cycle<dis; cycle++) {
			 for(int i=0; i<map.length; i++) {
				 for(int j=0; j<map[i].length; j++) {
					 copymap[j][map.length-i-1] = map[i][j];
				 }
			 }
			 for(int i=0; i<map.length; i++) {
				 for(int j=0; j<map[i].length; j++) {
					 map[i][j] = copymap[i][j];
				 }
			 }
			 if(check(copymap)) return true;
		 }
		 return false;
	 }
	 
	 static boolean check(int[][] map) {
		 boolean flag = false;
		 int holecheck = 0;
		 int keysize = map.length;
		 int limit = copyedlock.length-keysize+1;
		 
		 Outer : for(int i=0; i<limit; i++) {
			for(int j=0; j<limit; j++) {
				holecheck = 0;
				Loop : for(int m=0; m<keysize; m++) {
					for(int n=0; n<keysize; n++) {
						if(keysize-1<=m+i && keysize-1<=n+j && m+i<limit && n+j<limit) {
							if(copyedlock[m+i][n+j] == 0 && map[m][n] == 1) {
								holecheck++;
								continue;
							}
							if(copyedlock[m+i][n+j] == 1 && map[m][n] == 1) break Loop;
						}
					}
				}
				if(holecheck==hole) {
					flag = true;
					break Outer; 
				}
			}
		 }
		 return flag;
	 }
	 
	 
	 static void init() {
		 for(int i=0; i<visit.length; i++) {
			 for(int j=0; j<visit[i].length; j++) visit[i][j] = false;
		 }
	 }
	 static void print() {
		 for(int i=0; i<copymap.length; i++) {
			 for(int j=0; j<copymap[i].length; j++) System.out.print(copymap[i][j]+" ");
			 System.out.println();
		 }
		 System.out.println();
	 }
}


```

