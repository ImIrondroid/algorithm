# PRO_스킬트리


```java


import java.io.IOException;
import java.util.*;

class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		String[] arr = {"BACDE","CBADF","AECB","BDA"};
		System.out.println(s.solution("CBD",arr));
	}

	 public int solution(String skill, String[] skill_trees) {    
		 int answer = 0;
		 for(int i=0; i<skill_trees.length; i++) {
			 boolean[] visit = new boolean[skill.length()];
			 String skill_tree = skill_trees[i];
			 boolean flag = true;
			 Loop : for(int m=0; m<skill_tree.length(); m++) {
				 for(int n=0; n<skill.length(); n++) {
					 if(skill_tree.charAt(m)==skill.charAt(n)) {
						 for(int l=0; l<n; l++) if(!visit[l]) {
							 flag = false;
							 break Loop;
						 }
						 visit[n] = true;
					 }
				 }
			 }
			 if(flag) {
				 answer++;
			 }
		 }
		 return answer;
	 }
}


```

