# PRO_단체사진 찍기


```java


import java.io.IOException;
import java.util.*;


class Solution {
	

	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		String[] arr = {"N~F=0","R~T>2"};
		String[] arr1 = {"M~C<2","C~M>1"};
		String[] arr2 = {"N~F=2","A~T>5"};
		System.out.println(s.solution(1, arr));
	}

	char[] words = {'A','C','F','J','M','N','R','T'};
	char[] ret = new char[8];
	Map<Character, Integer> map = new HashMap<Character, Integer>();
	boolean[] visit = new boolean[8];
	int cnt = 0;
	
	public int solution(int n, String[] data) {
		
		dfs(data, 0);
		
		return cnt;
	}
	
	public void dfs(String[] data, int start) {
		if(start==8) {
			//for(int i=0; i<ret.length; i++) System.out.print(ret[i]+" ");
			//System.out.println(map.size());
			
			boolean flag = true;
			
			for(int i=0; i<data.length; i++) {
				int first = map.get(data[i].charAt(0));
				int second = map.get(data[i].charAt(2));
				int diff = Math.abs(second-first)-1;
				char operator = data[i].charAt(3);
				int third = data[i].charAt(4)-48;
				
				if(operator=='=') {
					if(diff==third) continue;
					else {flag = false; break;}
				} else if(operator=='>') {
					if(diff>third) continue;
					else {flag = false; break;}
				} else if(operator=='<') {
					if(diff<third) continue;
					else {flag = false; break;}
				}
			}
			
			if(flag) cnt++;
			
			return;
		}
		
		for(int i=0; i<8; i++) {
			if(!visit[i]) {
				visit[i] = true;
				ret[start] = words[i];
				map.put(words[i], start);
				dfs(data, start+1);
				map.remove(words[i]);
				visit[i] = false;
			}
		}
	}
}


```

