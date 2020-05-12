# PRO_문자열 압축


```java



import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStream;
import java.io.InputStreamReader;

public class Solution {

	static int Min = Integer.MAX_VALUE;
	
	public static int solution(String s) {
		
		for(int i=1; i<=s.length()/2; i++) {
			
			String result = "";
			int lastIndex = 0;
			int count = 1;
			
			//ooooooox에서 o부분만비교 하는 로직
			for(int j=0; j<s.length()-i; j+=i) {
				
				String left = s.substring(j,j+i);
				String right = "";
				
				//길이가 홀수건 짝수건 이 공식을 만족해야함
				if(s.length()-j>2*i) {
					right = s.substring(j+i,j+2*i);
				} else {
					right = s.substring(j+i, s.length());
					lastIndex = j+i;
				}
				
				if(left.equals(right)) {
					count++;
				} else {
					if(count>1) {
						result+=(count+left);
					} else {
						result+=left;
					}
					count = 1;
				}
			}
			
			//마지막 문자열 처리
			if(count>1) {
				result+=(count+s.substring(lastIndex, s.length()));
			} else {
				result+=(s.substring(lastIndex, s.length()));
			}
			
			//System.out.println("압축 단위 길이가 "+i+"일때 결과값 -> "+result);
			Min = Math.min(Min, result.length());
		}
		
		return Min;
	}
}



```

