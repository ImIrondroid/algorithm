# PRO_여행경로


```java


import java.util.*;


class Solution {

	public static void main(String[] args) {
		
		//https://programmers.co.kr/learn/courses/30/lessons/43164
		Solution solution = new Solution();
		String[][] arr1 = {{"ICN","JFK"},{"HND","IAD"},{"JFK","HND"}};
		String[][] arr = {{"ICN","SFO"},{"ICN","ATL"},{"SFO","ATL"}
							,{"ATL","ICN"},{"ATL","SFO"}};
		System.out.println(Arrays.asList(solution.solution(arr)).toString());
	}

	public static String[] ret;
	public static String[] last;
	
	public String[] solution(String[][] tickets) {
		
        boolean[] visit = new boolean[tickets.length];

        String[] answer = new String[tickets.length+1];
        ret = new String[tickets.length+1];
        last = new String[tickets.length+1];
        
        for(int i=0; i<tickets.length; i++) {
        	if(tickets[i][0].equals("ICN")) {
            	visit[i] = true;
            	ret[0] = "ICN";
            	dfs(tickets, visit, i, 1);
            	visit[i] = false;	
        	}
        }
        
        for(int i=0; i<last.length; i++) {
        	answer[i] = last[i];
        }
        
        return answer;
    }
	
	public void dfs(String[][] tickets, boolean[] visit, int now, int start) {
		if(start==tickets.length) {
			ret[tickets.length] = tickets[now][1];
			String retstr = Arrays.asList(ret).toString();
			String laststr = Arrays.asList(last).toString();
			if(last[0]==null) {
				for(int i=0; i<ret.length; i++) {
					last[i] = ret[i];
				}
			} else {
				for(int i=0; i<retstr.length(); i++) {
					if(retstr.charAt(i)<laststr.charAt(i)) {
						for(int k=0; k<ret.length; k++) {
							last[k] = ret[k];
						}
						break;
					} else if(retstr.charAt(i)>laststr.charAt(i)) {
						break;
					}
				}
			}
			return;
		}
		
		for(int i=0; i<tickets.length; i++) {
			if(!visit[i] && tickets[now][1].equals(tickets[i][0]) ) {
				visit[i] = true;
				ret[start] = tickets[now][1];
				dfs(tickets, visit, i, start+1);
				visit[i] = false;
			}
		}
	}
}


```

