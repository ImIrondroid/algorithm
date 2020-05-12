# PRO_N으로 표현


//DFS


```java


import java.io.IOException;
import java.util.*;

class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		System.out.println(s.solution(5, 12));
	}

	static int num;
	static int ret = Integer.MAX_VALUE;
	
	public int solution(int N, int number) {
        
        solve(N, 0, 0, number);
        
        if(ret==Integer.MAX_VALUE) return -1;
        else return ret;
    }
	
	public void solve(int N, int nCount, int pass, int target) {
		if(nCount>8) {
			return;
		}
		
		if(pass == target) {
			ret = Math.min(ret, nCount);
			return;
		}
		
		int num = N;
		int mul = N;
		
		for(int i=0; i<8-nCount; i++) {
			solve(N, nCount+i+1, pass + num, target);
			solve(N, nCount+i+1, pass - num, target);
			solve(N, nCount+i+1, pass * num, target);
			solve(N, nCount+i+1, pass / num, target);
			
			num = num*10+mul;
		}
	}
}


```

