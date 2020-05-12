# SWEA_간단한 369게임


```java


import java.util.*;


class Solution
{
	public static void main(String args[]) throws Exception {
		
		Scanner sc = new Scanner(System.in);
		StringBuilder sb = new StringBuilder();
		
		int T;
		
		T=sc.nextInt();
		
		for(int i=1; i<=T; i++) {
			String s = String.valueOf(i);
			int count = 0;
			for(int j=0; j<s.length(); j++) {
				if(s.charAt(j)-48!=0 && (s.charAt(j)-48)%3==0) count++;
			}
			if(count!=0) {
				for(int j=0; j<count; j++) sb.append("-");
				sb.append(" ");
			} else {
				sb.append(s+" ");
			}
		}
		
		System.out.println(sb);
	}
}


```

