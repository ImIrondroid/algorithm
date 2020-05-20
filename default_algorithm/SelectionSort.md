# 선택정렬 알고리즘 - Selection Sort


### 아이디어


'가장 작은 것을 선택해서 제일 앞으로 보내면 어떨까?'


### 특징


1. 자료 이동 횟수를 미리 결정한다.
2. 안정성이 없는 정렬이다. 이것은 같은 값이여도 상대적인 위치가 다를 수 있음을 의미한다.
3. Best일때 n^2, Worst일때도 n^2의 시간복잡도를 가진다.


### 그림


아래 그림은 선택정렬의 과정을 나타낸다. 

![](https://mblogthumb-phinf.pstatic.net/20140128_73/justant_1390835759169oepXz_PNG/1.png?type=w2)

그림참고 : https://m.blog.naver.com/PostView.nhn?blogId=justant&logNo=20203018572&proxyReferer=https%3A%2F%2Fwww.google.com%2F


```java


public class MySelectionSort {


    public MySelectionSort() {
        selection_sort();
    }
    
    public void selection_sort() {
        
        int[] arr = {1,2,3,0,10,3,4,5};
        
        int lth = arr.length;
        int min = 0;
        int temp = 0;
        int index = 0;
        for(int i=0; i<lth ; i++) {
            min = 10000000;
            for(int j=i; j<lth ; j++) {
                if(min > arr[j]) {
                    min = arr[j];
                    index = j;
                }
            }
            //최솟값과 i번째의 값과 교환
            temp = arr[index];
            arr[index] = arr[i];
            arr[i] = temp;
        }
        
        for(int item : arr) {
            System.out.println(item + " ");
        }
    }
}


```

