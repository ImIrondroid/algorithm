# PRO_[3차] 방금그곡


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		String[] arr = {"12:00,12:14,HELLO,C#DE#FGAB","13:00,13:07,WORLD,ABCDE#FG"};
		String[] arr1 = {"12:00,12:14,HELLO,C#DEFGAB", "13:00,13:05,WORLD,ABCDEF"};
		String[] arr2 = {"03:00,03:30,FOO,CC#B","04:00,04:08,BAR,CC#BCC#BCC#B"};
		System.out.println(s.solution("ABC",arr));
	}
	
	public String solution(String m, String[] musicinfos) {  
		StringTokenizer st;
		ArrayList<String> myMelody = getMelody(m);
		ArrayList<String> ret = new ArrayList<>();
		int mylth = myMelody.size();
		
		for(int i=0; i<musicinfos.length; i++) {
			st = new StringTokenizer(musicinfos[i], ",");
			
			String start = st.nextToken();
			String end = st.nextToken();
			String temp = st.nextToken();
			String melody = "";

			int difftime = getMin(start, end);
			if(difftime > 1439) difftime = 1439;

			ArrayList<String> compareMelody = getMelody(temp);
			
			if(difftime < compareMelody.size()) {
				for(int j=0; j<difftime; j++) melody += compareMelody.get(j);
			} else {
				melody = temp;
			}

			compareMelody = getMelody(melody);
			
			//멜로디 재생시간 길이 까지 맞춰 늘리기
			int index = 0;
			int init = compareMelody.size();
			
			for(int j=init; j<difftime; j++) {
				melody += compareMelody.get((index++)%init);
			}
			
			compareMelody = getMelody(melody);	
			
			//for(int j=0; j<compareMelody.size(); j++) System.out.print(compareMelody.get(j)+" ");
			//System.out.println();
			
			for(int j=0 ;j<=compareMelody.size()-mylth; j++) {
				String t = "";
				for(int l=0; l<mylth; l++) {
					t += compareMelody.get(j+l);
				}
				//System.out.println(t +" : "+m);
				if(t.equals(m)) {
					ret.add(musicinfos[i]);
					break;
				}
			}
			
		}

		Collections.sort(ret, new Comparator<String>() {
			@Override
			public int compare(String o1, String o2) {
				String arr[] = o1.split(",");
				int len1 = getMin(arr[0], arr[1]);
				arr = o2.split(",");
				int len2 = getMin(arr[0], arr[1]);
				return len2-len1;
			}
		});
		//System.out.println(ret.size());
		return ret.size() > 0 ? ret.get(0).split(",")[2] : "(none)";
	}
	
	public static int getMin(String startTime, String endTime) {
	    String[] arr;
	    arr = startTime.split(":");
	    int startMin = Integer.parseInt(arr[0]) * 60 + Integer.parseInt(arr[1]);
	    
	    arr = endTime.split(":");
	    int endMin = Integer.parseInt(arr[0]) * 60 + Integer.parseInt(arr[1]);
	    
	    return Math.abs(endMin-startMin);
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

