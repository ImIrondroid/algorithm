# PRO_전화번호 목록


```java


import java.io.IOException;
import java.util.*;

class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		String[] arr = {"1341","144","15"};
		System.out.println(s.solution(arr));
	}
	
	public boolean solution(String[] phone_book) {
        
		boolean answer = true;
        
        HashMap<String, Integer> hashMap = new HashMap<>();
        for(int i=0; i<phone_book.length; i++) {
        	String phone = phone_book[i];
        	for(int j=1; j<phone.length(); j++) {
        		hashMap.put(phone.substring(0,j), 1);
        	}
        }
        
        for(int i=0; i<phone_book.length; i++) {
        	if(hashMap.containsKey(phone_book[i])) {
        		answer = false;
        		break;
        	}
        }
        
        return answer;
    }
}


```

