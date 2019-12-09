# 버블정렬 알고리즘 - Bubble Sort


### Bubble Sort의 개념


1. 선택 정렬과 매우 유사한 알고리즘으로 직관적으로 받아들이기 쉬운 알고리즘이다.
2. 서로 인접한 두 원소끼리 비교하여 정렬하는 알고리즘이다.


### Bubble Sort의 과정


1. 아래 예시에서 list에 정렬전 배열 입력값을 받는다.
2. 이중 for문을 이용하여 안쪽 포문에서 j의 배열값과 j+1의 배열값을 비교한후에 큰 것을 오른쪽에 위치시키기 위해 swap을 한다.
3. 한 번 과정이 마무리되면 마지막 값은 제일 큰 값이 와있기때문에 다음과정에서는 1번 덜 시행하면 된다. 그러기 때문에 안쪽 for문에 i가 커질때마다 i의 값에 따라 덜 돌아야 하기때문에 j < len-i-1로 설정하였다.
4. 위의 과정을 반복한다.


### Bubble Sort의 특징


1. 구현이 매우 간단하다. 삽입정렬, 선택정렬과 비교해보면 코드가 더 짧다.
2. 모든 원소들을 비교하고 교환시킨다.
3. 최종 위치에 정렬된 원소라고해도 교환이 되는 일이 발생한다.
4. 선택정렬과 마찬가지로 Best일때 n^2, Worst일때도 n^2의 시간복잡도를 가진다.
5. 일반적으로 알고있는 정렬 알고리즘 중에 제일 많은 Run-time시간이 걸린다.



### 그림으로 표현한 Bubble Sort

아래 그림은 버블정렬의 과정을 나타낸다. 직관적으로 이해하기 매우 쉬운 알고리즘이다.

![](http://postfiles11.naver.net/20140128_282/justant_1390842794487v9kxH_PNG/%B9%F6%BA%ED%C1%A4%B7%C4.png?type=w2)

그림참고 : http://blog.naver.com/PostView.nhn?blogId=justant&logNo=20204028286&parentCategoryNo=&categoryNo=16&viewDate=&isShowPopularPosts=true&from=search


다음 아래 코드는 필자가 Java를 이용하여 버블정렬을 구현한 것이다. 


```java


public class MyBubbleSort {

    public MyBubbleSort() {
        bubble_sort();
    }
    
    public void bubble_sort() {
        
        int[] list = {1,3,2,6,3,4,-1,4,2,2,-99};
        int temp;
        int len = list.length;
        
        for(int i=0; i<len-1 ; i++) {
        
            temp = 0;
            
            for(int j=0 ; j< len-i-1 ; j++) {
            
                if(list[j] > list[j+1]) {
                
                    temp = list[j];
                    list[j] = list[j+1];
                    list[j+1] = temp;
                    
                }
            }
        }
        
        for(int item : list) {
        
            System.out.print(item + " ");
            
        }
    }
}


```

삽입정렬, 선택정렬도 쉬운 편에 속하지만 버블정렬이 조금 더 쉬운 느낌이 든다. 코드도 짧고 매우 직관적인 알고리즘이다.
