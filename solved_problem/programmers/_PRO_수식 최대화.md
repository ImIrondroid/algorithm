# PRO_수식 최대화


```java


import java.util.*;
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Solution {
	
	static List<Character> op = new ArrayList<>();
	static List<Character> minOp = new ArrayList<>();
	static List<Long> num = new ArrayList<>();
	static boolean[] check;
	static char[] opArr;
	
	static List<Character> copyedOp = new ArrayList<>();
	static List<Character> copyedMinOp = new ArrayList<>();
	static List<Long> copyedNum = new ArrayList<>();
	
	static long answer = 0L;
    
	public long solution(String expression) {
		
        StringTokenizer st = new StringTokenizer(expression, "-*+");
        
        while(st.hasMoreTokens()) {
        	num.add(Long.parseLong(st.nextToken()));
        }
        
        Set<Character> set = new HashSet<>();
        for(int i=0; i<expression.length(); i++) {
        	char ch = expression.charAt(i);
        	if(ch == '-' || ch == '*' || ch == '+') {
        		if(!set.contains(ch)) {
        			set.add(ch);
        			minOp.add(ch);
        		}
        		op.add(ch);
        	}
        }
        
        check = new boolean[minOp.size()]; //연산자 우선순위 종류만큼
        opArr = new char[minOp.size()];
        
        dfs(0);
        
        return answer;
    }
	
	static void dfs(int start) {
		if(start == minOp.size()) {
			//op조합
			copyedNum.addAll(num);
			copyedOp.addAll(op);
			
			for(int i=0; i<opArr.length; i++) copyedMinOp.add(opArr[i]);
			
			while(!copyedMinOp.isEmpty()) {
				char ch = copyedMinOp.get(0);
				for(int i=0; i<copyedOp.size(); i++) {
					if(copyedOp.get(i) == ch) {
						if(ch == '-') {
							copyedNum.set(i, copyedNum.get(i) - copyedNum.get(i+1));
						} else if(ch == '+') {
							copyedNum.set(i, copyedNum.get(i) + copyedNum.get(i+1));
						} else {
							copyedNum.set(i, copyedNum.get(i) * copyedNum.get(i+1));
						}
						copyedNum.remove(i+1);
						copyedOp.remove(i);
						i--;
					}
				}
				copyedMinOp.remove(0);
			}
			
			answer = Math.max(answer, Math.abs(copyedNum.get(0)));
			copyedNum.remove(0);
			
			return;	
		}
		
		for(int i=0; i<minOp.size(); i++) {
			if(!check[i]) {
				check[i] = true;
				opArr[start] = minOp.get(i);
				dfs(start+1);
				check[i] = false;
			}
		}
	}
}


```

