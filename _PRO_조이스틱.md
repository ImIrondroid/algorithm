# PRO_조이스틱


```java


import java.io.IOException;
import java.util.*;

class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		System.out.println(s.solution("ABABA"));
	}

	public int solution(String name) {
		int answer = 0;

		//입력 값 name중 가장 긴 ASequence의 길이, index 시작, 끝 위치를 구함.
		int finalSequence = Integer.MIN_VALUE;
		int finalStart = 0;
		int finalEnd = 0;
		
		int aSequence = 0;
		int indexStart = -1;
		int indexEnd = -1;
		for(int i=0; i<name.length(); i++) {
			if(name.charAt(i)=='A') {
				aSequence++;;
				if(indexStart==-1) indexStart = i;
				indexEnd = i;
			} else {
				if(aSequence > finalSequence) {
					finalSequence = aSequence;
					finalStart = indexStart;
					finalEnd = indexEnd;
				}
				indexStart = -1;
				indexEnd = -1;
				aSequence = 0;
			}
		}
		if(aSequence!=0) {
			if(aSequence > finalSequence) {
				finalSequence = aSequence;
				finalStart = indexStart;
				finalEnd = indexEnd;
			}
		}
		
		//각 알파벳을 바꾸는데 필요한 조이스틱 조작횟수
		for(int i=0; i<name.length(); i++) {
    	
			int moveLeft = 0;
			int moveRight = 0;
			char nowAlphabet = name.charAt(i);
        
			moveLeft = (int) nowAlphabet - 65;
			moveRight = 26 - moveLeft;
    	
			if(moveLeft>moveRight) answer += moveRight;
    		else answer += moveLeft;
		}

		//쭉 지나갈 때, 왼쪽 턴 1번 했을때, 오른쪽 턴 1번 했을때 조작 횟수 최솟값
		int leftlth = finalStart;
		int rightlth = name.length()-finalEnd-1;
		int max = Integer.MAX_VALUE;
		
		if(finalSequence!=0) {
			max = Math.min(max, name.length()-1+answer);
			if(finalStart!=0) max = Math.min(max, 2*leftlth-2+rightlth+answer);
			max = Math.min(max, 2*rightlth-1+leftlth+answer);
			
			return max;
		} else {
			return answer+name.length()-1;
		}
	}
}


```

