# 스택 - Stack


### 아이디어


택배 상하차와 같은 자료구조


### 특징


먼저 들어온 데이터가 더 늦게 나갈 수 있다.


### 구현


```java


class MyStack implements StackMethods{

	private int[] arr;
	int pos = 0;
	
	public MyStack(int size) {
		this.arr = new int[size];
	}
	
	@Override
	public boolean empty() {
		if(pos==0) {
			return true;
		} 
		return false;
	}

	@Override
	public void push(int input) {
		arr[pos++] = input;
		return;
	}

	@Override
	public void pop() {
		if(empty()) {
			System.out.println(-1);
			return;
		}
		System.out.println(arr[--pos]);
		return;
	}

	@Override
	public void top() {
		if(empty()) {
			System.out.println(-1);
			return;
		}
		System.out.println(arr[pos-1]);
		return;
	}

	@Override
	public void size() {
		System.out.println(pos);
		return;
	}

}

interface StackMethods {
	boolean empty();
	void push(int input);
	void pop();
	void top();
	void size();
}


```

