# PRO_[1차] 프렌즈 4블록


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();
		String[] arr1 = {"HGNHU","CRSHV","UKHVL","MJHQB","GSHOT","MQMJJ","AGJKK","QULKK"};
		String[] arr = {"CCBDE", "AAADE", "AAABF", "CCBBF"};
		System.out.println(solution.solution(8,5,arr1));
	}
	 
	static char[][] map;
	static boolean[][] visit;
	
	public int solution(int m, int n, String[] board) {
	     
		map = new char[m][n];
		visit = new boolean[m][n];
		
		for(int i=0; i<m; i++) {
			String line = board[i];
			for(int j=0; j<n; j++) {
				map[i][j] = line.charAt(j);
			}
		}
		
		int answer = 0;
	    
		while(true) {
			
			for(int i=0; i<m-1; i++) {
				for(int j=0; j<n-1; j++) {
					if(map[i][j]!='X')
						visitMap(i,j);
				}
			}
			
			
			int blocks = check(m,n);
			if(blocks==0) break;
			else {
				answer+=blocks; //지울 블록의 갯수 더해줌
				clearandmove(m,n); //블록 다시 검사전으로 셋팅
			}
		}
		
		return answer; 
	}
	
	public void clearandmove(int m, int n) {
		
		for(int i=0; i<m; i++) {
			for(int j=0; j<n; j++) {
				if(visit[i][j]) {
					visit[i][j] = false;
					map[i][j] = '*';
				}
			}
		}
		
		StringTokenizer st;
		String temp = "";
		
		for(int i=n-1; i>=0; i--) {
			for(int j=m-1; j>=0; j--) {
				temp+=map[j][i];
			}
			st = new StringTokenizer(temp,"*");
			temp = "";
			while(st.hasMoreTokens()) {
				temp+=st.nextToken();
			}
			for(int j=temp.length()-1; j<m-1; j++) {
				temp+="X";
			}
			for(int j=m-1; j>=0; j--) {
				map[j][i] = temp.charAt(temp.length()-1-j);
			}
			temp = "";
		}
	}
	
	public int check(int m, int n) {
		int sum = 0;
		for(int i=0; i<m; i++) {
			for(int j=0; j<n; j++) {
				if(visit[i][j]) sum++;
			}
		}
		return sum;
	}
	
	public void visitMap(int i, int j) {
		if(map[i][j]==map[i+1][j] 
				&& map[i+1][j]==map[i][j+1] 
						&& map[i][j+1]==map[i+1][j+1]) {
			for(int k=i; k<i+2; k++) {
				for(int l=j; l<j+2; l++) {
					visit[k][l] = true;
				}
			}
		}
	}
} 


```

