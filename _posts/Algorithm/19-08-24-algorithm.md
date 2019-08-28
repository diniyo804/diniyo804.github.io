---
layout: post
title: level 1 - 최대공약수, 최소공배수 
category: 알고리즘
tags: [algorithm, 최대공약수, 최소공배수, gcd, 유클리드]
comments: true
---

## 문제
```text
두 수를 입력받아 최대공약수와 최소공배수를 반환하는 함수를 완성해 보세요.
배열의 맨 앞에 최대공약수, 그다음 최소공배수를 넣어 반환하면 됩니다.
예를 들어 두 수 3, 12의 최대공약수는 3, 최소공배수는 12이므로 solution(3, 12)는 [3, 12]를 반환해야 합니다.
  
제한 사항
두 수는 1이상 1000000이하의 자연수입니다.
    
입출력 예
자연수 2와 5의 최대공약수는 1, 최소공배수는 10이므로 [1, 10]을 리턴해야 합니다.
자연수 3와 12의 최대공약수는 3, 최소공배수는 12이므로 [3, 12]을 리턴해야 합니다.
```



## 풀이
```java
    public static int[] solution(int n, int m) {
  
        int large = (n > m) ? n : m;
        int small = (n < m) ? n : m;
        int max = 1;
        int min =1;
  
        int[] numArr = new int[small];
  
        for (int i=0; i<small; i++){
            numArr[i] =i+1;
        }
        
        //최대공약수  
        for (int num : numArr){
            if (small%num==0 && large%num==0 ) {
                if (max < num) {
                    max = num;
                }
            }
        }
  
        int[] numArr2 = new int[large];

        for (int i=0; i<numArr2.length; i++){
            numArr2[i] = i+1;
        }
 

        //최소공배수
        for(int num : numArr2) {
            if (small*num == large) {
                min = large; 
                break;
            }else if (num == large) {
                min = small*large; 
                break;   
            }
        }
        return new int[]{max, min};
    }

```

## 다른 풀이
```java
    public static int[] newSolution(int n, int m) {
    
        int large =(n > m)? n : m;
        int small=(n < m) ?n :m;
  
        int max = getGCD(large,small);//최대공약수 => 나머지가 0이 될 때까지 나눈다.
        int min = n*m/max; //최소공배수
  
        return new int[]{max, min};
    }
  
    private static int getGCD(int large, int small) {
        if (large % small == 0) return small;
        return getGCD(small,large%small);
    }

```

  
## 테스트 코드
```java
    @org.junit.Test
    public void solution() {
        int[] result ={3,12};
        assertArrayEquals(result, skillCheck2.newSolution(3,12));
    }
```

### 정리
유클리드 호제법을 이용한 최대공약수 알고리즘이 기존에 존재한다.   
GCD(greatest Common divisor) 알고리즘이라고도 부른다.  
```text
유클리드 호제법이란, 정수 n과 m (전제:n>m)을 비교해서 n을 m으로 나눈 나머지 r이 0보다 크면 다시 m을 r로 나누어 나머지를 구한다.   
이 방법을 반복해 나머지(r)이 0이 될 때의 m이 최대 공약수가 된다.
  
[12, 3]으로 예를들면 12(n)를 3(m)으로 나누면 나머지는 0(r)이다.  
즉 12와 3의 최대공약수는 3이다.
  
[11, 4]로 예를 들면 11을 4로 나누면 나머지는 3이다.  
4를 3으로 나누면 나머지는 1이다.  
3을 1로 나누면 나머지는 0이다.   
즉 최대공약수는 1이다.  
```
최소공배수는 최대공약수를 이용해 구할 수 있다.  
최소공배수 = m*n / 최대공약수

이런 방법을 알아둔다면 나중에 비슷한 문제를 풀 때 큰 도움이 될 것 같다.   
오늘같은 풀이가 또다시 반복되지 않도록 기억해두자! 
  
문제출처  
> [프로그래머스](https://programmers.co.kr/skill_checks)