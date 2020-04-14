# PRO_뉴스 클러스터링


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		System.out.println(s.solution("aa1+aa2","AAAA12"));
	}

	//https://readystory.tistory.com/65
	public int solution(String str1, String str2) {
	    
		int answer = 0;
		List<String> left = new ArrayList<>();
		List<String> right = new ArrayList<>();
		for(int i=0; i<str1.length()-1; i++) {
			char leftstr = str1.charAt(i);
			char rightstr = str1.charAt(i+1);
			if(check(leftstr) && check(rightstr)) {
				String input = String.valueOf(leftstr) + String.valueOf(rightstr);
				left.add(input.toLowerCase());
			}
		}
		for(int i=0; i<str2.length()-1; i++) {
			char leftstr = str2.charAt(i);
			char rightstr = str2.charAt(i+1);
			if(check(leftstr) && check(rightstr)) {
				String input = String.valueOf(leftstr) + String.valueOf(rightstr);
				right.add(input.toLowerCase());
			}
		}

		//http://theeye.pe.kr/archives/1499
		int topCount = 0;
		List<String> larger = (left.size() > right.size()) ? left : right;
		List<String> smaller = (larger == left) ? right : left;
		for(Iterator<String> it = smaller.iterator(); it.hasNext();) {
			String str = it.next();
			if(larger.contains(str)) {
				larger.remove(str);
				it.remove();
				topCount++;
			}
		}
		
		int bottomCount = left.size()+right.size()+topCount;
		if(topCount==0 && bottomCount==0) return 65536;
		else {
			answer = (int) ((topCount / (double) bottomCount) * 65536);
			return answer;
		}
	 
	}
	
	public boolean check(char alphabet) {
		if((alphabet >= 'A' && alphabet <= 'Z') ||
				(alphabet >= 'a' && alphabet <= 'z')) {
			return true;
		}
		return false;
	}
}


```

