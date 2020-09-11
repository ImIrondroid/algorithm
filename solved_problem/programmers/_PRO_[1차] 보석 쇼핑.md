# PRO_보석 쇼핑


```java


import java.util.*;
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Solution {
	
	public int[] solution(String[] gems) {
        int[] answer = {};
        
        int left = 0, right = 0;
        int curLeft = 0, curRight = 0;
        int size = new HashSet<>(Arrays.asList(gems)).size();
        int compare = Integer.MAX_VALUE; //최소 거리를 구하기 위함
        
        Map<String, Integer> map = new HashMap<String, Integer>();
        
        while(true) {
        	if(map.size() == size) {
        		map.put(gems[left], map.get(gems[left]) - 1);
        		if(map.get(gems[left]) == 0) {
        			map.remove(gems[left]);
        		}
        		left++;
        	} else {
            	if(right == gems.length) break;
            	
        		//해시맵 사이즈가 해시셋의 사이즈와 같아질 때 까지 넣기
        		map.put(gems[right], map.getOrDefault(gems[right], 0) + 1);
        		right++;
        	}
        	
        	if(map.size() == size && compare > right - left) {
        		compare = right - left;
        		curLeft = left + 1;
        		curRight = right;
        	}
        }
        
        return new int[] {curLeft, curRight};
    }
	
	static class sc {
		
		private static BufferedReader br;
		private static StringTokenizer st;

		static void init() {
			br = new BufferedReader(new InputStreamReader(System.in));
			st = new StringTokenizer("");
		}

		static String readLine() {
			try {
				return br.readLine();
			} catch (IOException e) {
				System.out.println(e.getMessage());
			}
			return null;
		}

		static String readLineReplace() {
			try {
				return br.readLine().replaceAll("\\s+", "");
			} catch (IOException e) {
				System.out.println(e.getMessage());
			}
			return null;
		}

		static String next() {
			while (!st.hasMoreTokens()) {
				try {
					st = new StringTokenizer(br.readLine());
				} catch (IOException e) {
					System.out.println(e.getMessage());
				}
			}
			return st.nextToken();
		}

		static long nextLong() {
			return Long.parseLong(next());
		}

		static int nextInt() {
			return Integer.parseInt(next());
		}

		static double nextDouble() {
			return Double.parseDouble(next());
		}
	}
}


```

