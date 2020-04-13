# PRO_[1차] 캐시


```java


import java.util.*;


import java.io.IOException;
import java.util.*;

class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		String[] arr = {"Aaaa","AB","AB","AB","AAaaa","CC"};
		System.out.println(s.solution(3, arr));
	}

	public int solution(int cacheSize, String[] cities) {
		
		  if(cacheSize==0) return 5*cities.length;
	      int answer = 0;
	      
	      ArrayList<String> list = new ArrayList<String>();
	      
	      for(int i=0; i<cities.length; i++) {
	    	  String city = cities[i].toLowerCase();
	    	  if(list.size() < cacheSize) {
	    		  if(list.isEmpty()) {
    				  list.add(city);
    				  answer += 5;
	    		  } else {
		    		  boolean check = false;
	    			  for(int j=0; j<list.size(); j++) {
		    			  if(list.get(j).equals(city)) {
		    				  list.remove(j);
		    				  list.add(city);
		    				  check = true;
		    				  break;
		    			  }
		    		  }
	    			  if(check) {
	    				  answer += 1;
		    		  } else {
		    			  list.add(city);
		    			  answer += 5;
		    		  }
	    		  } 
	    	  } else {
	    		  boolean check = false;
		    	  for(int j=0; j<list.size(); j++) {
		    		  if(list.get(j).equals(city)) {
		    			  list.remove(j);
		    			  list.add(city);
		    			  check = true;
		    			  break;
		    		  }
		    	  }
		    	  if(!check) {
		    		  answer += 5;
			    	  list.remove(0);
			    	  list.add(city);
		    	  } else {
		    		  answer += 1;
		    	  }
	    	  }
	      }
	      return answer;
	  }
}


```

