# SWEA_패턴 마디의 길이


```java


import java.util.*;


class Solution {
	public static void main(String args[]) throws Exception {
		
		Scanner sc = new Scanner(System.in);
		StringBuilder sb = new StringBuilder();
		
		int T;
		
		T=sc.nextInt();
		
		for(int i=1; i<=T; i++) {
			
			String line = sc.next();
			String sub = "";
			char temp = line.charAt(0);
			for(int j=1; j<line.length(); j++) {
				if(line.charAt(j)==temp) {
					sub = line.substring(0, j);
					if(sub.equals(line.subSequence(j, 2*j))) {
						System.out.println("#"+i+" "+sub.length());
						break;
					} else {
						continue;
					}
				}
			}
		}
		
		System.out.println(sb);
	}
}


```

