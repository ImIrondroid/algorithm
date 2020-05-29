# 큐 - Queue


### 아이디어


은행창구에서 일어나는 상황과 같은 자료구조


### 특징


먼저 들어온 데이터가 먼저 나갈 수 있다.


### 구현


```java


class QueueImpl implements Queue {
	
	private int[] arr = null;
	private int begin = 0;
	private int end = 0;
	private int count = 0;
	
	public QueueImpl(int size) {
		this.arr = new int[size];
	}
	
	@Override
	public boolean isEmpty() {
		return (begin==end) ? true : false;
	}
	
	@Override
	public void push(int num) {
		arr[end++] = num;
		count++;
	}

	@Override
	public void pop() {
		if(isEmpty()) {
			System.out.println(-1);
			return;
		}
		count--;
		System.out.println(arr[(begin++)%arr.length]);
	}

	@Override
	public void size() {
		System.out.println(count);
	}

	@Override
	public void front() {
		if(isEmpty()) {
			System.out.println(-1);
			return;
		} 
		System.out.println(arr[begin]);
	}

	@Override
	public void back() {
		if(isEmpty()) {
			System.out.println(-1);
			return;
		} 
		System.out.println(arr[end-1]);
	}
	
}

interface Queue {
	
	boolean isEmpty();
	void push(int num);
	void pop();
	void size();
	void front();
	void back();
}


```

