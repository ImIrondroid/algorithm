# PRO_숫자 게임


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		int[] A = {5,1,3,7};
		int[] B = {2,2,6,8};
		System.out.println(s.solution(A,B));
	}

	public int solution(int[] A, int[] B) {
        int answer = 0;
        
        Arrays.sort(A); //1357
        Arrays.sort(B); //2268
        
        int idx = B.length-1;
        
        for(int i=A.length-1; i>=0; i--) {
        	if(A[i]<B[idx]) {
        		idx--;
        		answer++;
        	}
        }
        
        return answer;
    }
}


```

