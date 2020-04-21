# PRO_[3차] 방금그곡


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		String[] arr = {"12:00,12:14,HELLO,CDEFGAB","13:00,13:05,WORLD,ABCDEF"};
		String[] arr1 = {"12:00,12:14,HELLO,C#DEFGAB", "13:00,13:05,WORLD,ABCDEF"};
		String[] arr2 = {"03:00,03:30,FOO,CC#B","04:00,04:08,BAR,CC#BCC#BCC#B"};
		System.out.println(s.solution("CC#BCC#BCC#BCC#B",arr2));
	}
	
	int priority = -1;
	int maxDiffTime = Integer.MAX_VALUE;
	String retTitle = "";
	
	public String solution(String m, String[] musicinfos) {  
		String answer = "";
		StringTokenizer st;
		int mlth = m.length();
		ArrayList<String> myMelody = getMelody(m);
		
		for(int i=0; i<musicinfos.length; i++) {
			st = new StringTokenizer(musicinfos[i], ",");
			
			String start = st.nextToken();
			String end = st.nextToken();
			String title = st.nextToken();
			String melody = st.nextToken();
			String temp = melody;
			
			int melth = melody.length();
			int difftime = getMins(start, end);

			ArrayList<String> compareMelody = getMelody(melody);
			
			if(mlth <= melth) {
				for(int j=0; j<melth-mlth; j++) {
					String t = melody.substring(j, melth);
					if(t.startsWith(m)) return title;
				}
			}

			//멜로디 재생시간 길이 까지 맞춰 늘리기
			int index = 0;
			int init = compareMelody.size();
			for(int j=init; j<init+myMelody.size()-1; j++) {
				melody += compareMelody.get((index++)%init);
			}

			compareMelody = getMelody(melody);
			
			for(int j=0; j<compareMelody.size(); j++) {
				System.out.print(compareMelody.get(j)+" ");
			}
			System.out.println();
			
			
			
		}
	    
	    if(maxDiffTime == Integer.MAX_VALUE) answer = "'(None)'";
	    else answer = retTitle;
		return answer;
	}
	
	public int getMins(String start, String end) {
		StringTokenizer st;
		
		st = new StringTokenizer(start, ":");
		int startHour = Integer.valueOf(st.nextToken());
		int startMin = Integer.valueOf(st.nextToken());
		
		st = new StringTokenizer(end, ":");
		int endHour = Integer.valueOf(st.nextToken());
		int endMin = Integer.valueOf(st.nextToken());

		int dif = endHour - startHour;
		int ret = dif*60;
		if(startMin <= endMin) {
			ret += endMin - startMin;
		} else {
			ret += (60+endMin - startMin) - 60;
		}
		return ret;
	}
	
	public ArrayList<String> getMelody(String m) {
		ArrayList<String> list = new ArrayList<>();
		for(int i=0; i<m.length(); i++) {
			if(m.charAt(i)=='#') continue;
			if(m.charAt(i) >= 'A' && m.charAt(i) <= 'G') {
				if(i==m.length()-1) {
					if(m.charAt(i) != '#') {
						list.add(String.valueOf(m.charAt(i)));
						break;
					}
				} else {
					if(m.charAt(i+1) == '#') {
						list.add(String.valueOf(m.charAt(i)) + String.valueOf(m.charAt(i+1)));
					} else {
						list.add(String.valueOf(m.charAt(i)));
					}
				}		
			}
		}
		return list;
	}
}


```

