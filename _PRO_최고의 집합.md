# PRO_최고의 집합


```java


//풀이 및 번외 DFS 중복 집합 구현


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		System.out.println(s.solution(2,8));
	}

	public int[] solution(int n, int s) {
		
		if(n>s) return new int[] {-1};
		if(n==1) return new int[] {s};

		int[] answer = new int[n];
		int div = s/n;
		int rest = s%n;
		
		for(int i=0; i<n; i++) answer[i] = div;
		for(int i=n-1; ; i--) { 
			if(rest==0) break;
			answer[i]++;
			rest--;
		}
		
		return answer;
	}

	static Map<String, Integer> hash = new HashMap<>();
	
	public int[] solution1(int n, int s) {
	    List<Integer> list = new ArrayList<>();
	    
		dfs(1, n, s, list);

		int[] answer = new int[n];
		int max = Integer.MIN_VALUE;
		int compare, num, idx;
		Iterator<String> it = hash.keySet().iterator();
		
		while(it.hasNext()) {
			String str = it.next();
			compare = 1;
			idx = 0;
			
			//원소의 곱 구하기
			for(int i=0; i<str.length(); i++) {
				num = str.charAt(i)-48;
				if(num >= 0 && num <=9) {
					compare *= num;
				}
			}
			//원소의 곱이 max값보다 크면
			if(max < compare) {
				max = compare;
				for(int i=0; i<str.length(); i++) {
					num = str.charAt(i)-48;
					if(num >= 0 && num <=9) {
						answer[idx++] = num;
					}
				}
			}
		}
		
		if(max == Integer.MIN_VALUE) return new int[] {-1};
		else return answer;
	}
	
	static int[] arr;
	
	static void dfs(int start, int limit, int pass, List<Integer> list) {
		
		if(pass<0) return;
		
		if(start==limit) {
			list.add(pass);
			
			arr = new int[list.size()];
			for(int i=0; i<list.size(); i++) {
				arr[i] = list.get(i);
			}
			
			Arrays.sort(arr);
			String s = Arrays.toString(arr);
			if(hash.get(s)==null) {
				//System.out.println(s);
				hash.put(s, 1);
			}
			
			list.remove(list.size()-1);
			return;
		}
		
		for(int i=1; i<pass/2+1; i++) {
			list.add(i);
			dfs(start+1, limit, pass-i, list);
			list.remove(list.size()-1);
		}
	}
}



```

