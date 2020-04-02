# PRO_크레인 인형뽑기 게임


```java


import java.util.*;

public class Solution {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Solution solution = new Solution();

		int[][] board = {
				{0,0,0,0,0},{0,0,1,0,3},{0,2,5,0,1},{4,2,4,4,2}, {3,5,1,3,1}
		};
		int[] moves = {1,5,3,5,1,2,1,4};
		System.out.println(solution.solution(board,moves));
	}
	
	static ArrayList<Integer> list = new ArrayList<>();
	static int removeCount = 0;
	
	public int solution(int[][] board, int[] moves) {
        
		int[][] mBoard = board;
		
		for(int i=0; i<moves.length; i++) {
			int line = moves[i];
			int topOfLine = getTop(mBoard, line-1);
			if(topOfLine!=-1) {
				//인형 존재함
				list.add(mBoard[topOfLine][line-1]);
				check(list);
				mBoard[topOfLine][line-1] = 0;
			} else {
				//비어있는 상태
				continue;
			}
		}
		
		int answer = removeCount;
        
        return answer;
    }
	
	public int getTop(int[][] board, int num) {
		
		int index = -1;
		int[][] temp = board;
		
		for(int i=0; i<board.length; i++) {
			if(board[i][num]!=0) {
				index = i;
				break;
			}
		}
		
		if(index==-1) {
			return -1;
		} else {
			return index;
		}
	}
	
	public void check(ArrayList<Integer> list) {
		int top = list.size()-1;
		//2개이상 연속 인형이 있을 때
		if(list.size()>1) {
			if(list.get(top)==list.get(top-1)) {
				list.remove(top);
				list.remove(top-1);
				removeCount+=2;
			}
		}
	}
}


```

