# PRO_[1차] 다트게임


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();
		System.out.println(solution.solution("1D2S3T*"));
	}
	public int solution(String dartResult) {
	     
		int answer = 0;
		int index = 0;
		
		String[] operator = new String[3];
		String[] alphabet = new String[3];
		int[] num = new int[3];
		
		StringTokenizer st = new StringTokenizer(dartResult,"1234567890");
		alphabet[0] = st.nextToken();
		alphabet[1] = st.nextToken();
		alphabet[2] = st.nextToken();
		
		for(int i=0; i<dartResult.length(); i++) {
			if(dartResult.charAt(i)>='0' && dartResult.charAt(i)<='9') {
				if(dartResult.charAt(i)=='1' && dartResult.charAt(i+1)=='0') {
					num[index] = 10;
					i++;
					System.out.print(num[index]+" ");
					System.out.println(alphabet[index]);
					index++;
				} else {
					num[index] = dartResult.charAt(i)-48;
					System.out.print(num[index]+" ");
					System.out.println(alphabet[index]);
					index++;
				}
			}
		}
		
		for(int i=0; i<3; i++) {
			if(alphabet[i].length()==2) {
				if(alphabet[i].substring(0,1).equals("S")) {
					num[i] = (int) Math.pow(num[i], 1);
					operator[i] = alphabet[i].substring(1,2);
				} else if(alphabet[i].substring(0,1).equals("D")) {
					num[i] = (int) Math.pow(num[i], 2);
					operator[i] = alphabet[i].substring(1,2);
				} else if(alphabet[i].substring(0,1).equals("T")) {
					num[i] = (int) Math.pow(num[i], 3);
					operator[i] = alphabet[i].substring(1,2);
				}
			} else {
				if(alphabet[i].equals("S")) {
					num[i] = (int) Math.pow(num[i], 1);
				} else if(alphabet[i].equals("D")) {
					num[i] = (int) Math.pow(num[i], 2);
				} else if(alphabet[i].equals("T")) {
					num[i] = (int) Math.pow(num[i], 3);
				}
			}
		}
		
		for(int i=0; i<3; i++) {
			if(operator[i]!=null && operator[i].equals("*")) {
				if(i==0) {
					num[i] *= 2;
				} else {
					for(int j=i-1; j<=i; j++) {
						num[j] *=2;
					}
				}
			} else if(operator[i]!=null && operator[i].equals("#")) {
				num[i] *= -1;
			} else continue;
		}
		
		for(int i=0; i<3; i++) {
			answer+=num[i];
		}
		
		return answer;
	 
	}
} 


```

