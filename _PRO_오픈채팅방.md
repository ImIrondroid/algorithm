# PRO_오픈채팅방


```java


import java.io.IOException;
import java.util.*;

class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		String[] arr = {"Enter uid1234 Muzi", "Enter uid4567 Prodo","Leave uid1234",
				"Enter uid1234 Prodo", "Change uid4567 Ryan"};
		System.out.println(s.solution(arr));
	}

	public String[] solution(String[] record) {
		StringTokenizer st;
        
        ArrayList<Message> list = new ArrayList<>();
        HashMap<String, String> hashMap = new HashMap<>();
        for(int i=0; i<record.length; i++) {
        	st = new StringTokenizer(record[i]);
        	String status = st.nextToken();
        	String id = st.nextToken();
        	if(status.equals("Leave")) {
            	list.add(new Message(status, id));
            	System.out.println(status+" "+id);
        	} else {
            	String nick = st.nextToken();	
            	if(status.equals("Change")) {
            		hashMap.replace(id, nick);
            	} else if(status.equals("Enter")) {
                	if(!hashMap.containsKey(id)) hashMap.put(id, nick);
                	else hashMap.replace(id, nick);
                	list.add(new Message(status, id));
                	System.out.println(status+" "+id);
            	} 
        	}
        }
        
        String[] answer = new String[list.size()];
        
        for(int i=0; i<list.size(); i++) {
        	Message message = list.get(i);
        	if(message.status.equals("Enter")) {
        		String str = hashMap.get(message.id)+"님이 들어왔습니다.";
        		answer[i] = str;
        	} else {
        		String str = hashMap.get(message.id)+"님이 나갔습니다.";
        		answer[i] = str;
        	}
        }
        
        return answer;
    }
}

class Message {
	String status;
	String id;
	Message(String status, String id) {
		this.status = status;
		this.id = id;
	}
}


```

