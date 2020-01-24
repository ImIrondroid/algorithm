# 삽입정렬 알고리즘 - Insertion Sort


### Insertion Sort의 개념


1. 변수 하나를 이용하여 정렬을 실시한다.
2. 배열의 모든 요소를 선택된 배열왼쪽의 값부터 역순으로 차례대로 비교하여, 값이 들어갈 위치를 찾아 삽입하여 정렬하는 알고리즘이다. 여기서 제일 중요한 개념은 선택된 값의 왼쪽은 정렬된 상태인 것이다.


### Insertion Sort의 과정


1. 아래 예시에서 list에 정렬전 배열 입력값을 받는다.
2. temp는 swap을 위한 변수이고 안쪽 for문에서 사용되는 j는 바깥포문에서도 사용될 것이기때문에 바깥쪽에 선언되었다.
3. i는 1부터시작하며 안쪽 for문에서 i-1과 비교하는것부터 시작하며 index는 0으로 향할때까지 반복된다. list[j]가 temp에 저장된 값 보다 크면 오른쪽으로 한칸씩 이동시킨다. 그렇지 않으면  for문을 멈춘다.
4. j-- 된 상태이기때문에 list[j+1]에 temp를  넣어준다. 이 상태는 정렬된 상태이다.
4. 위의 과정을 반복한다.


### Insertion Sort의 특징


1. 레코드 수가 적을수록 알고리즘 자체가 간단하기때문에 유리할 수 있다.
2. Best일때 n, Worst일때 n^2의 시간복잡도를 가진다. 정렬인 상태일때 비교만 이루어지기 때문이다.
3. 레코드들이 대부분 정렬되어있을때 효율적인 알고리즘일 수 있다.


### 그림으로 표현한 Insertion Sort


아래 그림은 삽입정렬의 과정을 나타낸다. 선택된 배열값 왼쪽의 값들이 이미 정렬되어있는 상태라고 생각하고 보면 이해가 잘 될것이다.

![](https://mblogthumb-phinf.pstatic.net/20140128_138/justant_1390838207680eBQJX_PNG/1.png?type=w2)

그림참고 : https://m.blog.naver.com/PostView.nhn?blogId=justant&logNo=20204025251&proxyReferer=https%3A%2F%2Fwww.google.com%2F


다음 아래 코드는 필자가 Java를 이용하여 삽입정렬을 구현한 것이다. 


```java

public class MyInsertionSort {

    public MyInsertionSort() {
        insertion_sort();
    }
    
    public void insertion_sort() {
        
        int[] list = {1,4,3,2,5,5,9,10};
        int length = list.length;
        int temp = 0;
        int j;
        
        for(int i=1 ; i<length ; i++) {
            temp = list[i];
            
            //앞에부분은 정렬이 되어있다는 것을 보장함
            for(j=i-1 ; j>=0 && list[j]>temp ; j-- ) {
                list[j+1] = list[j];
            }
            
            list[j+1] = temp;
        }
        
        for(int i : list) {
            System.out.println(i+ " ");
        }
    }
}


```

