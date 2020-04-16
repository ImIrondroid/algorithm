# PRO_소수 찾기(2)


//에라토스테네스 체 이용


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		System.out.println(s.solution("17"));
	}

	char[] arr;
	boolean[] visit;
	boolean[] check;
	
	public int solution(String numbers) {
        int answer = 0;
        arr = numbers.toCharArray();
        visit = new boolean[numbers.length()];
        check = new boolean[10000000];
        
        for(int i=2; i<check.length; i++) {
        	check[i] = true;
        }
        for(int i=2; i*i<check.length; i++) {
        	for(int j=i*i; j<check.length; j+=i) {
        		check[j] = false;
        	}
        }
        
    	Set<Integer> set = new HashSet<>();
        for(int i=1; i<=numbers.length(); i++) {
        	solve(set, 0, 0, i);
        }
        
        Iterator<Integer> it = set.iterator();
        while(it.hasNext()) {
        	int num = it.next();
        	//System.out.println(num + " " + check[num]);
        	if(check[num]) answer++;
        }
        
        return answer;
    }
	
	public void solve(Set<Integer> set, int num, int start, int end) {
		if(start==end) {
			set.add(num);
			return;
		}
		
		for(int i=0; i<arr.length; i++) {
			if(!visit[i]) {
				int toss = arr[i]-48;
				visit[i] = true;
				solve(set, num*10+toss, start+1, end);
				visit[i] = false;
			}
		}
	}
}


```

