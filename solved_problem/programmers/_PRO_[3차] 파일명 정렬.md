# PRO_[3차] 파일명 정렬


```java


import java.io.IOException;
import java.util.*;


class Solution {
	
	public static void main(String[] args) throws IOException {
		
		Solution s = new Solution();
		String[] arr = {"A-10 Thunderbolt ll", "B-50 Superfortress","F-5 Freedom Fighter","F-14 Tomcat"};
		String[] arr1 = {"img12.png", "img10.png","img02.png","img1.png","IMG01.GIF","img2.JPG"};
		String[] arr2 = {"F-15","A123","a1234","BBA01","BBA11","bbA12","BBA12"};
		System.out.println(s.solution1(arr2));
	}
	
	public String[] solution1(String[] files) {
		String[] answer = new String[files.length];
		List<File> list = new ArrayList<File>();
		for(int i=0; i<files.length; i++) {
			String[] f = extract(files[i]);
			System.out.println(f[0]+" "+ f[1]+"  "+ f[2]);
			list.add(new File(f[0], f[1], f[2]));
		}
		
		Collections.sort(list, new Comparator<File>() {
			@Override
			public int compare(File o1, File o2) {
				String lefthead = o1.head.toLowerCase();
				String righthead = o2.head.toLowerCase();
				int idx = 0;
				int smallidx = (lefthead.length() < righthead.length())? lefthead.length() : righthead.length();
				while(idx != smallidx) {
					if(lefthead.charAt(idx) < righthead.charAt(idx)) return -1;
					else if(lefthead.charAt(idx) > righthead.charAt(idx)) return 1;
					idx++;
				}
				if(lefthead.length() < righthead.length()) return -1;
				else if(lefthead.length() > righthead.length()) return 1;
				else {
					String leftnum = o1.num;
					int removedLeftnum = Integer.valueOf(removeFirstAllZero(leftnum));
					String rightnum = o2.num;
					int removedRightnum = Integer.valueOf(removeFirstAllZero(rightnum));
					System.out.println(o1.toString()+ "     "+o2.toString()+"     "+removedLeftnum+"   "+removedRightnum);
					
					if(removedLeftnum < removedRightnum) return -1;
					else if(removedLeftnum > removedRightnum) return 1;
					else return 0;
				}
			}
		});
		
		
		for(int i=0; i<list.size(); i++) {
			System.out.print(list.get(i).toString()+"  ");
			answer[i] = list.get(i).toString();
		}
		System.out.println();
		return answer;
	}

	public String[] extract(String file) {
		String[] answer = new String[3];
		int headindex = 0;
		for(int i=0; i<file.length(); i++) {
			if(file.charAt(i) >= '0' && file.charAt(i) <= '9') {
				answer[0] = file.substring(0, i);
				headindex = i;
				break;
			}
		}
		int numindex = -1;
		for(int i=headindex; i<file.length(); i++) {
			if(file.charAt(i) < '0' || file.charAt(i) > '9') {
				answer[1] = file.substring(headindex, i);
				numindex = i;
				break;
			}
		}
		if(numindex==-1) {
			answer[1] = file.substring(headindex, file.length());
			answer[2] = "";
		} else {
			answer[2] = file.substring(numindex, file.length());
		}
		return answer;
	}
	
	public String removeFirstAllZero(String s) {	
		int index = -1;
		for(int i=0; i<s.length(); i++) {
			if(s.charAt(i)=='0') continue;
			else {
				index = i;
				break;
			}
		}
		if(index == -1) return "0";
		return s.substring(index, s.length());
	}
}

class File {
	String head;
	String num;
	String tail;
	File(String head, String num, String tail) {
		this.head = head;
		this.num = num;
		this.tail = tail;
	}
	
	@Override
	public String toString() {
		return head+num+tail;
	}
}


```

