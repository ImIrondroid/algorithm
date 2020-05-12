# PRO_가장 긴 팰린드롬


//효율성 중요한 문제


```java


import java.io.IOException;
import java.util.*;

class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		System.out.println(s.solution("abababa"));
	}

	public int solution(String s) {
	       
		for(int i=s.length(); i>=2; i--) {
			for(int j=0; j<=s.length()-i; j++) {
				int start = j;
				int end = j+i;
				boolean flag = true;
				for(int m=0; m<i/2; m++) {
					if(s.charAt(start+m) == s.charAt(end-1-m)) continue;
					else {flag = false; break;}
				}
				if(flag) return i;
			}
		}
		return 1;
    }
	
	//시간초과
	public int search(String s) {
		for(int i=s.length(); i>=2; i--) {
			if(check(s, i)) return i;
			else continue;
		}
		return 1;
	}

	public boolean check(String s, int lth) {
		for(int i=0; i<=s.length()-lth; i++) {
			String str = s.substring(i, i+lth);
			if(isSame(str)) return true;
			else continue;
		}
		return false;
	}
	
	public boolean isSame(String s) {
		
		for(int i=0; i<s.length()/2; i++) {
			if(s.charAt(i) == s.charAt(s.length()-i-1)) continue;
			else return false;
		}
		return true;
	}
}


```

