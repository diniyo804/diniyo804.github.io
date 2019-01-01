---
layout: post
title: Java - 상속의 기본문법,접근제어 지시자
category: Java
tags: [java]
comments: true
---

## 1. 상속의 기본 특성 
상속은 기존 클래스에 메소드와 변수를 추가하여 새로운 클래스를 정의하는 것이다.

## 2. 용어정리 : 상위 클래스와 하위 클래스
상속 관계에서 상속을 받은 클래스를 '하위클래스(sub class)', '유도 클래스(derived class)'라 부르고,
상속의 대상이 된 클래스를 가리켜 '상위 클래스(super class)' 또는 '기초 클래스(base class)'라 부른다.

## 3. 상속 예시
```java
//base class
Class Man{
    public String name;
    public void callName() { System.out.println("My name is " + name); }
}
```
```java
//sub class
Class BusinessMan extends Man{
    public String company;    
    public void callInfo() { System.out.println("My compane is " + company ); }
}
```
하위 클래스의 인스턴스를 만들면 상위 클래스에 정의되어있는 메서드와 변수에 접근할 수 있다.  
인스턴스 생성 시 상위 클래스의 멤버가 함께 포함되기 때문이다.


## 4. 상속과 생성자
- 인스턴스 변수의 초기화는 그 변수가 선언된 클래스를 통해 하는 것이 가장 좋은 모델이다.  
만약 인스턴스 변수 초기화가 해당 클래스에서 이뤄지지 않으면, 
그 클래스를 상속하는 모든 하위 클래스에서 상위클래스의 모든 인스턴스 변수를 초기화 해야한다. 

- 따라서 상위클래스의 인스턴스 변수는 상위 클래스의 생성자 내에서 초기화 하고, 
단지 하위 클래스에서는 상위 클래스의 변수를 초기화하는데 필요한 값을 **super**를 
통해 전달만 하는 것이 합리적이다.


## 5. 상위 클래스의 생성자 호출 super!
```java
super(1,2,3);
//상위 클래스의 생성자를 호출하면서, 1,2,3을 매개변수로 전달한다!
```

## 6. 상속한 클래스의 인스턴스의 생성 과정
```java
new BusinessMan("Mr.Hong", "Hybrid", "Staff Eng.");
```
위 문장에 의해 제일 먼저 메모리 공간의 할당과 모든 인스턴스 변수의 디폴트 초기화가 일어난다.
그 다음 상위클래스+하위클래스 형태의 인스턴스가 생성된다.  
**생성자는 인스턴스 생성 과정에서 인스턴스 변수의 초기화를 위해 딱 한번만 호출될 뿐, 
인스턴스 내에 계속해서 존재하는 메서드는 아니다.**

```java
Class BusinessMan extends Man {
    public String company;    
    
    public BusinessMan(String name, String company) {
        super(name);
        this.company = company;
    }    
    public void show() { System.out.println("My compane is " + company ); }
}

```
위에서 보듯, 우선 하위 클래스의 생성자가 호출된다. 그러나 생성자 내부의 super문에 의해 
상위 클래스의 생성자가 먼저 실행된다.
비록 하위 클래스의 생성자가 인자의 전달을 위해 먼저 호출되지만, 실행은 상위 클래스의 생성자가 먼저 이뤄진다.
결과적으로 상위 클래스의 멤버가 먼저 초기화되었다.
상위 클래스의 생성자 실행이 완료되면, 하위 클래스의 생성자가 실행된다.


## 7. 반드시 호출되어야 하는 상위 클래스의 생성자
하위 클래스의 생성자 내부에서는 반드시 상위 클래스의 생성자가 호출되어야 한다.
만약 하위 클래스가 상위 클래스의 생성자를 호출할 수 없는 구조로 되어있다면, 하위 클래스의 인스턴스 생성은 불가능하다.

```java
public class Inheritance_test {
    public static void main(String[] args) {
        BBB bb = new BBB();

    }
}

class  AAA {
    int num1;
    public AAA(){
        System.out.println("AAA생성자 실행");
    }
}

class BBB extends AAA{
    int num2;
    public BBB(){}

}
```
BBB 클래스를 보면 자동으로 디폴트 생성자는 추가되지 않는다. 하지만 상위 클래스의 생성자 호출을 위한 super문이 없다.
이 경우 컴파일 단계에서 상위 클래스 생성자 호출을 위한 super문이 자동으로 삽입된다.
즉 위 클래스 생성자 내에는 다음과 같이 super문이 추가된다.
```java
clasee BBB extends AAA{
    int num2;
    BBB(){
        super();    //자동으로 삽입된 super
        num2=0;
    }
}
```
