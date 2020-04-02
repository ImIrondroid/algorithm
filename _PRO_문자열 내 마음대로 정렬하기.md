# PRO_문자열 내 마음대로 정렬하기


//정렬


```java


import java.util.*;

public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();

		String[] strs = {"abce","abcdd","cdx"};
		System.out.println(solution.solution(strs, 2));
	}
	
	static String[] temp = new String[50];
	
	public String[] solution(String[] strings, int n) {
	      
		String[] answer = mergeSort(strings, 0, strings.length-1, n);
	     
		for(int i=0; i<answer.length; i++) {
			System.out.print(answer[i]+" ");
		}
		return answer;
	  
	}
	
	public String[] mergeSort(String[] strings, int left, int right, int index) {
		
		String[] answer = null;
		
		if(left<right) {
			int mid = (left+right)/2;
			mergeSort(strings,left,mid,index);
			mergeSort(strings,mid+1,right,index);
			answer = merge(strings,left,mid,right,index);
		}
		
		return answer;
	}
	
	public String[] merge(String[] strings, int left, int mid, int right, int index) {
		
		int i=left;
		int k=left;
		int j=mid+1;
		
		while(i<=mid && j<=right) {
			if(strings[i].charAt(index)<strings[j].charAt(index)) {
				temp[k++] = strings[i++];
			} else if(strings[i].charAt(index)==strings[j].charAt(index)) {
				int start = 0;
				int shortlth = 0;
				if(strings[i].length()>=strings[j].length()) shortlth = strings[j].length();
				else shortlth = strings[i].length();
				
				while(start!=shortlth) {
					if(strings[i].charAt(start)<strings[j].charAt(start)) {
						temp[k++] = strings[i++];
						break;
					} else if(strings[i].charAt(start)>strings[j].charAt(start)) {
						temp[k++] = strings[j++];
						break;
					}
					start++;
				}
				if(start==shortlth) {
					if(strings[i].length()<strings[j].length()) {
						temp[k++] = strings[i++];
					} else {
						temp[k++] = strings[j++];
					}
				}
			} else {
				temp[k++] = strings[j++];
			}
		}
		
		if(i>mid) {
			for(int m=j; m<=right; m++, k++) {
				temp[k] = strings[m];
			}
		} else {
			for(int m=i; m<=mid; m++, k++) {
				temp[k] = strings[m];
			}
		}
		
		for(int m=left; m<=right; m++) {
			strings[m] = temp[m];
		}
		
		return strings;
	}
}


```

