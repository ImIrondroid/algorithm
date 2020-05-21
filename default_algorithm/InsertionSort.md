# 삽입정렬 알고리즘 - Insertion Sort


### 아이디어


'각 숫자를 적절한(필요할 때만) 위치에 삽입하면 어떨까?'


### 특징


1) 대부분 정렬되어있을때 효율적인 알고리즘이다.
2) 필요할 때만 위치를 바꾸기 때문에 버블, 선택 정렬보다 더 빠르게 작동한다.
3) Best일때 n, Worst일때 n^2의 시간복잡도를 가진다. 정렬인 상태일때 비교만 이루어지기 때문이다.


### 그림


![](https://mblogthumb-phinf.pstatic.net/20140128_138/justant_1390838207680eBQJX_PNG/1.png?type=w2)

림참고 : https://m.blog.naver.com/PostView.nhn?blogId=justant&logNo=20204025251&proxyReferer=https%3A%2F%2Fwww.google.com%2F


```java


public class MyInsertionSort {

    public MyInsertionSort() {
        insertion_sort();
    }
    
    public void insertion_sort() {
        
        int[] arr = {1,4,3,2,5,5,9,10};
        int lth = arr.length;
        int temp = 0;
        int j;
        
        for(int i=0 ; i<lth-1 ; i++) {
           j=i;
           while(j>=0 && arr[j]>arr[j+1]) {
        	   temp = arr[j];
        	   arr[j] = arr[j+1];
        	   arr[j+1] = temp;
        	   j--;
           }
        }
        
        for(int i : arr) {
            System.out.println(i+ " ");
        }
    }
}


```

