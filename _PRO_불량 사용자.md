# PRO_불량 사용자


//DFS


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {

		Solution solution = new Solution();
		
		//https://programmers.co.kr/learn/courses/30/lessons/64064
		String[] user_id = {"frodo","fradi","crodo","abc123","frodoc"};
		String[] banned_id = {"fr*d*","*rodo","******","******"};
		System.out.println(solution.solution(user_id, banned_id));
	}
	
	static ArrayList<String[]> list = new ArrayList<>();
	static boolean[] visit = new boolean[8];
	
	public int solution(String[] user_id, String[] banned_id) {
	  
		
		int answer = 0;
		int cycle = user_id.length;
		StringTokenizer st;
	     
		dfs(user_id, banned_id, 0, "");
		
		answer = list.size();		
		return answer;
	   
	}
	
	public void dfs(String[] user_id, String[] banned_id, int start, String ret) {
		
		if(start==banned_id.length) {
			System.out.println(ret.trim());
			if(list.size()==0) 	list.add(ret.trim().split(" "));
			else {
				int check = 0;
				for(int i=0; i<list.size(); i++) {
					String[] arr = list.get(i);
					String[] compare = ret.trim().split(" ");
					Arrays.sort(arr);
					Arrays.sort(compare);
					if(Arrays.equals(arr, compare)) continue;
					else check++;
				}
				if(check==list.size()) list.add(ret.trim().split(" "));
			}
			return;
		}
		
		for(int i=0; i<user_id.length; i++) {
			if(!visit[i]) {
				String user = user_id[i];
				String ban = banned_id[start];
				int banNum = 0;
				for(int j=0; j<ban.length(); j++) {
					if(ban.charAt(j)=='*') banNum++;
				}
				if(user.length()==ban.length()) {
					int sameCount = 0;
					int index = 0;
					while(index!=ban.length()) {
						if(user.charAt(index)==ban.charAt(index)) sameCount++;
						index++;
					}
					if(ban.length()-banNum == sameCount) {
						visit[i] = true;
						dfs(user_id, banned_id, start+1, ret+" "+user);
						visit[i] = false;
					}
				}
			}
		}
	}
}


```

