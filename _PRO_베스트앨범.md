# PRO_베스트앨범


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		String[] genres = {"classic","pop","classic","classic","pop"};
		int[] plays = {500,600,150,800,2500};
		System.out.println(s.solution(genres, plays));
	}

	public int[] solution(String[] genres, int[] plays) {
		
        Map<String, Integer> map = new HashMap<>();
        Queue<Point> queue = new PriorityQueue<Point>();
        ArrayList<Integer> list = new ArrayList<>();
        
        for(int i=0; i<genres.length; i++) {
        	if(map.get(genres[i])==null) map.put(genres[i], plays[i]);
        	else map.replace(genres[i], map.get(genres[i])+plays[i]);
        }
        Iterator<String> it = map.keySet().iterator();
        while(it.hasNext()) {
        	String s = it.next();
        	queue.add(new Point(s, map.get(s), 0));
        }
        
        while(!queue.isEmpty()) {
        	Point p = queue.poll();
        	String g = p.genre;
        	ArrayList<Point> al = new ArrayList<>();
        	//같은 장르인 것들 al에 넣기
        	for(int j=0; j<genres.length; j++) {
        		if(g.equals(genres[j])) {
        			al.add(new Point(g, plays[j], j));
        		}
        	}
        	//al 내림차순 정렬 후 2개만 list에 집어넣기
        	Collections.sort(al);
        	if(al.size()>=2) {
        		for(int j=0; j<2; j++) list.add(al.get(j).index);
        	} else {
        		list.add(al.get(0).index);
        	}
        }

        int[] answer = new int[list.size()];
        
        for(int i=0; i<list.size(); i++) {
        	answer[i] = list.get(i);
        	//System.out.println(answer[i]);
        }
        
        return answer;
    }
}

class Point implements Comparable<Point> {
	String genre;
	int replay;
	int index;
	Point(String genre, int replay, int index) {
		this.genre = genre;
		this.replay = replay;
		this.index = index;
	}
	
	@Override
	public int compareTo(Point o) {
		if(this.replay < o.replay) return 1;
		else if(this.replay > o.replay) return -1;
		return 0;
	}
}


```

