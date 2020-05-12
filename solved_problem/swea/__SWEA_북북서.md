# SWEA_북북서


```java


import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.StringTokenizer;

class Main
{
	public static void main(String args[]) throws Exception {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st;
	
		int T = Integer.valueOf(br.readLine());

		for(int test_case = 1; test_case <= T; test_case++) {
			
			ArrayList<String> list = new ArrayList<>();
			String input = br.readLine();
			for(int i=0; i<input.length(); i++) {
				if(input.charAt(i)=='n') list.add("north");
				else if(input.charAt(i)=='w') list.add("west");
			}
			
			int rightTop = 0;
			int rightBottom = 1;
			int operator = 0; //0 = 더하기, 1 = 빼기
			int count = 0;
			
			for(int i=list.size()-1; i>=0; i--) {
				if(i==list.size()-1) {
					if(list.get(i).equals("west")) {
						rightTop = 90;
						operator = 1;
					}
				} else {
					String next = list.get(i);
					if(next.equals("north")) operator = 1;
					else operator = 0;
					int nextNumTop = 0;
					int nextNumBottom = 0;
					
					nextNumTop = 90;
					nextNumBottom = (int) Math.pow(2, ++count);
					if(operator==1) {
						if(nextNumBottom > rightBottom) {
							int divide = nextNumBottom / rightBottom;
							rightTop = divide * rightTop;
							rightBottom = nextNumBottom;
							rightTop = Math.abs(rightTop - nextNumTop);
						} else {
							int divide = rightBottom/nextNumBottom;
							nextNumTop = divide * nextNumTop;
							nextNumBottom = rightBottom;
							rightTop = Math.abs(rightTop - nextNumTop);
						}
					} else if(operator==0) {
						if(nextNumBottom > rightBottom) {
							int divide = nextNumBottom / rightBottom;
							rightTop = divide * rightTop;
							rightBottom = nextNumBottom;
							rightTop = Math.abs(rightTop + nextNumTop);
						} else {
							int divide = rightBottom/nextNumBottom;
							nextNumTop = divide * nextNumTop;
							nextNumBottom = rightBottom;
							rightTop = Math.abs(rightTop + nextNumTop);
						}
					}
				}
			}
			while(rightTop%2==0 && rightBottom%2==0) {
				rightTop/=2; rightBottom/=2;
			}
			if(rightTop==0) System.out.println("#"+test_case+" "+0);
			else if(rightBottom==1) System.out.println("#"+test_case+" "+rightTop); 
			else {
				System.out.println("#"+test_case+" "+rightTop+"/"+rightBottom);
			}
		}
	}
}


```

