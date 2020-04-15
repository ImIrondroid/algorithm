# PRO_후보키


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		String[][] arr = {{"100","ryan","music","2"},
				{"200","apeach","math","2"},
				{"300","tube","computer","3"},
				{"400","con","computer","4"},
				{"500","muzi","music","3"},
				{"600","apeach","music","2"}};
		String[][] arr1 = {{"a","b","c","aa","bb"},
				{"a","c","b","ab","ac"},
				{"b","d","c","ac","ad"},
				{"c","c","aa","ae","acc"}};
		String[][] arr2 = {
				{"ab","c"},{"a","bc"},{"x","yz"},{"x","c"}
		};
		System.out.println(s.solution(arr2));
	}

	static List<String> list = new ArrayList<>();
	static List<Set<String>> sets = new ArrayList<Set<String>>();
	static boolean[] visit;
	
	public int solution(String[][] relation) {
        int answer = 0;
        visit = new boolean[relation[0].length];
        for(int i=1; i<=relation[0].length; i++) {
        	solve(relation, -1, 0, i);
        }
        answer = list.size();
        return answer;
    }
	
	public void solve(String[][] arr, int compare, int start, int end) {
		if(start == end) {	
			HashSet<String> set = new HashSet<>();
			//튜플 식별 가능한지 확인
			for(int i=0; i<arr.length; i++) {
				String temp = "";
				for(int j=0; j<visit.length; j++) {
					if(visit[j]) temp += arr[i][j];
				}
				if(!temp.equals("")) set.add(temp);
			}
			
			//식별 가능하다면
			if(set.size() == arr.length) {
				String input = "";
				for(int i=0; i<visit.length; i++) {
					if(visit[i]) {
						input += String.valueOf(i);
					}
				}
				if(list.size()==0) {
					list.add(input);
					System.out.println(input);
				} else {
					for(int i=0; i<list.size(); i++) {
						String temp = list.get(i);
						if(!check(input, temp)) {
							return;
						}
					}
					System.out.println(input);
					list.add(input);
				}
			}
			return;
		}
		
		for(int i=0; i<arr[0].length; i++) {
			if(!visit[i] && compare<i) {
				visit[i] = true;
				solve(arr, i, start+1, end);
				visit[i] = false;
			}
		}
	}
	
	public boolean check(String input, String temp) {
		int count = 0;
		int compare = temp.length();
		if(input.length() > temp.length()) {
			for(int i=0; i<input.length(); i++) {
				for(int j=0; j<temp.length(); j++) {
					if(input.charAt(i)==temp.charAt(j)) {
						count++;
						continue;
					}
				}
			}
		}
		if(count == compare) return false;
		else return true;
	}
}


```

