---
layout: post
title: level 1 - 두 정수 사이의 합
category: 알고리즘
tags: [등차수열]
comments: true
---
    
## 문제
```text
두 정수 a, b가 주어졌을 때 a와 b 사이에 속한 모든 정수의 합을 리턴하는 함수를 완성하세요.
예를 들어 a = 3, b = 5인 경우, 3 + 4 + 5 = 12이므로 12를 리턴합니다.
  
제한 사항
1. a와 b가 같은 경우는 둘 중 아무 수나 리턴하세요.
2. a와 b는 -10,000,000 이상 10,000,000 이하인 정수입니다.
3. a와 b의 대소관계는 정해져있지 않습니다.
  
입출력 예
a    	b	   return
3    	5	     12
3	    3    	  3
5	    3	     12


```



## 풀이
```java
    public static long solution(int a, int b) {
        long answer = 0;
        int maximum = 10000000;
        int minimum = -10000000;
  
        if (a == b) return a;
        if (a > maximum || b > maximum) return 0;
        if (a < minimum || b < minimum) return 0;
  
        int large = (a > b) ? a : b;
        int small = (a < b) ? a : b;
  
        for (int i=small; i<=large; i++){
            answer += i;
            System.out.println("answer :" + answer);
        }
  
        return answer;

    }

```

## 다른 풀이
```java
   public static long newSolution(int a, int b) {
        long answer;
        int maximum = 10000000;
        int minimum = -10000000;
  
        if (a == b) return a;
        if (a > maximum || b > maximum) return 0;
        if (a < minimum || b < minimum) return 0;
  
        int large = (a > b) ? a : b;
        int small = (a < b) ? a : b;
  
        answer = sumSmallToLarge(large,small);
  
        return answer;
    }
  
    private static long sumSmallToLarge(int large, int small) {
        return (large - small + 1) * (large + small) / 2;
    }
  
```

  
## 테스트 코드
```java
    @Test
    public void testCheck (){
        //같은 수 입력 시 그대로 리턴
        assertEquals(3,Level1.solution(3,3));
  
        //a와 b는 -10,000,000이상 10,000,000이하인 정수
        assertEquals(0, Level1.solution(-10000001, 4));
        assertEquals(0, Level1.solution(10800001, 4));
        assertEquals(12, Level1.solution(3,5));
        assertEquals(12, Level1.solution(5,3));
    }

```

### 정리
나는 for문을 이용해 두 정수 사이의 값을 1씩 증가시키면서 결과값을 계산하도록 구현했는데  
등차수열의 합 원리를 이용한 간단한 풀이를 찾을 수 있었다.  
나의 풀이의 경우 두 정수 사이 숫자의 개수만큼 for문을 반복해야 한다.  
예를들어 1부터 100까지의 합을 구할 경우 for문 또한 100번을 돌아야 하기때문에 효율적이지 않다.  
하지만 다른풀이의 공식을 이용하면 1번의 연산으로 결과값을 얻을 수 있다.  
여기서 알아두어야 할 개념은 가우스의 원리를 이용한 등차수열의 합 개념이다.
수학쪽 개념이 빈약해서 저 공식을 봤을 때 바로 이해가 되지는 않았다. 공부가 필요할 것 같다.     
간단해보이는 문제라도 수학과 알고리즘 측면에서 접근하면 훨씬 더 효율적인 코드를 짤 수 있는 것 같다.   

  
문제출처  
> [프로그래머스](https://programmers.co.kr/skill_checks)