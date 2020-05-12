# PRO_위장


```java


import java.util.*;


public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();
		String[][] arr = {{"yellow_hat","headgear"},{"blue_sunglasses","eyewear"},{"green_turban","headgear"}};
		System.out.println(solution.solution(arr));
	}
	
	static int ret = 0;
	
	public int solution(String[][] clothes) {
        
		HashMap<String, Integer> hashMap = new HashMap<>();
		
		int answer = 0;
		
		for(int i=0; i<clothes.length; i++) {
			String type = clothes[i][1];
			if(hashMap.get(type)==null) {
				hashMap.put(type, 1);
			} else {
				hashMap.replace(type, hashMap.get(type)+1);
			}
		}
		
		ArrayList<Integer> list = new ArrayList<>();
		Iterator<String> iterator = hashMap.keySet().iterator();
		
		while(iterator.hasNext()) {
			String key = iterator.next();
			list.add(hashMap.get(key));
		}

		if(list.size()==30) return (int) Math.pow(2, 30)-1;
		
		boolean[] visit = new boolean[list.size()];
		for(int i=0; i<list.size(); i++) {
			dfs(list, visit, -1, 0, i+1);
		}
		
		answer = ret;
		
        return answer;
    }
	
	public void dfs(ArrayList<Integer> list, boolean[] visit, int compare, int start, int end) {
		if(start==end) {
			//System.out.println(getSum(list, visit));
			ret += getSum(list, visit);
		}
		
		for(int i=0; i<list.size(); i++) {
			if(!visit[i] && i>compare) {
				visit[i] = true;
				dfs(list, visit, i, start+1, end);
				visit[i] = false;
			}
		}
	}
	
	public int getSum(ArrayList<Integer> list, boolean[] visit) {
		int sum = 1;
		for(int i=0; i<visit.length; i++) {
			if(visit[i] == true) sum*=list.get(i);
		}
		return sum;
	}
} 


```

