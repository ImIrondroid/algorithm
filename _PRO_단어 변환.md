# PRO_단어 변환


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		String[] arr = {"hot","dot","dog","lot","log","cog"};
		String[] arr1 = {"hot","dot","dog","lot","log"};
		System.out.println(s.solution("hit","cog", arr1));
	}

	boolean[] visit = new boolean[50];
	
	public int solution(String begin, String target, String[] words) {
        int answer = bfs(words, begin, target);
        
        return answer;
    }
	
	public int bfs(String[] words, String begin, String target) {
		Queue<Point> queue = new LinkedList<Point>();
		queue.add(new Point(begin, 0));
		int nochange = 0;
		int cnt = 0;
		
		Loop : while(!queue.isEmpty()) {
			Point now = queue.poll();
			for(int i=0; i<words.length; i++) {
				String compare = words[i];
				if(now.word.equals(target)) {
					cnt = now.val;
					break Loop;
				}
				if(now.word.length() != compare.length()) continue;
				if(visit[i]) continue;
				if(!check(compare, now.word)) {
					nochange++;
					continue;
				}
				else {
					queue.add(new Point(compare, now.val+1));
					//System.out.println(now.word +"  "+compare +"  "+now.val);
					visit[i] = true;
				}
			}
		}
		if(nochange==words.length) return 0;
		else return cnt;
	}
	
	public boolean check(String begin, String now) {
		int cnt = 0;
		
		if(begin.length() != now.length()) return false;
		
		for(int i=0; i<begin.length(); i++) {
			if(begin.charAt(i) != now.charAt(i)) cnt++;
			if(cnt>1) return false;
		}
		return true;
	}
}

class Point {
	String word;
	int val;
	Point(String word, int val) {
		this.word = word;
		this.val = val;
	}
}


```

