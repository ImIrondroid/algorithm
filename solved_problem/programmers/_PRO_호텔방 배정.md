# PRO_호텔방 배정

```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		long[] arr = {1,1,1,1,1};
		System.out.println(s.solution(10, arr));
	}

	public long[] solution(long k, long[] room_number) {
        long[] answer = new long[room_number.length];
        Map<Long, Long> hash = new HashMap<Long, Long>();
        for(int i=0; i<room_number.length; i++) {
        	long roomNum = room_number[i];
        	if(!hash.containsKey(roomNum)) {
        		hash.put(roomNum, roomNum+1);
        		answer[i] = roomNum;
        	}
        	else {
        		ArrayList<Long> list = new ArrayList<Long>();
        		while(hash.containsKey(roomNum)) {
        			list.add(roomNum);
        			roomNum = hash.get(roomNum);
        		}
        		for(int j=0; j<list.size(); j++) {
        			hash.replace(list.get(j), roomNum+1);
        		}
        		hash.put(roomNum, roomNum+1);
        		answer[i] = roomNum;
        	}
        }
        
        //for(int i=0; i<room_number.length; i++) System.out.print(answer[i]+" ");
        //System.out.println();  
        return answer;
    }
}


```

