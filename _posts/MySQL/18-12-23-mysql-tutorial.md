---
layout: post
title: MySQL - MySql개념과 데이터 타입
category: MySql
tags: [MySql, 데이터베이스]
comments: true
---

### MySQL의 개요
데이터베이스는 정보를 저장하는 데에 특화된 애플리케이션/시스템이다.   
단순히 정보를 파일에 저장하는 것보다, 훨씬 더 많은 기능을 제공한다.  
오늘날 대부분의 데이터들이 데이터베이스에 저장되고 있다.  

MySql은 전 세계적으로 가장 널리 사용되고 있는 데이터베이스로 오픈소스이며 무료이다.  
많은 웹 애플리케이션이 MySql을 기본 데이터베이스로 사용하고 있다.  
  

### 데이터베이스 언어의 3가지 형태
1. [DDL(Data Define Language)](https://ko.wikipedia.org/wiki/%EB%8D%B0%EC%9D%B4%ED%84%B0_%EC%A0%95%EC%9D%98_%EC%96%B8%EC%96%B4)
 : 데이터를 정의하는 언어(create, alter, drop, truncate)
2. [DML(Data Manipulation Language)](https://ko.wikipedia.org/wiki/%EB%8D%B0%EC%9D%B4%ED%84%B0_%EC%A1%B0%EC%9E%91_%EC%96%B8%EC%96%B4)
 : 데이터를 처리,조작하는 언어 (insert, update, select, delete) 
3. [DCL(Data Control Language)](https://ko.wikipedia.org/wiki/%EB%8D%B0%EC%9D%B4%ED%84%B0_%EC%A0%9C%EC%96%B4_%EC%96%B8%EC%96%B4)
 : 데이터에 대한 액세스를 제어하기 위한 언어 (grant, revoke)


### 데이터 타입

| <center>type | <center>바이트 수 | <center>범위 | <center>설명 |
| :------- | :------- | :------- | :------- |
| **숫자 형식** | 
| INT() | 4 | 약 -21억 ~ +21억 | 정수형 |
| BIGINT() | 8 | 약-900경 ~ +900경 | 정수형 |
| FLOAT | 4 | 소수점 아래 7자리까지 표현 | 부동소수점 (12.1242) |
| DOUBLE | 8 | 소수점 아래 15자리까지 표현 | 부동소수점 |
| **문자 형식** | 
| CHAR(n) | ? | 최대 255글자 | 고정길이 문자형. n은 글자수. CHAR=CHAR(1). |
| VARCHAR(n) | ? | 최대 65535글자 | 가변길이 문자형. Variable Character. 용량 절약에 유리 |
| BINARY(n) | 1~255 | | 고정길이 이진 데이터 값 |
| VARBINARY(n) | 1~255 | | 가변길이 이진 데이터 값 |
| TINYTEXT | | | 최대 255글자 | 
| TEXT | | 최대 65535글자| 글 본문 |
| **날짜 형식** |
| DATE | 3 | | YYYY-MM-DD |
| DATETIME | 8 | | YYYY-MM-DD HH:MM:SS |
| TIME | 3 | | HH:MM:SS |
| TIMESTAMP | 4 | | 이후로 지난 시간 | 


**CHAR와 VARCHAR는 UTF-8의 형태를 지니므로 입력한 글자의 언어에 따라 내부적으로 크기가 달라진다.**  
**따라서 CHAR(100)은 한글 영어 상관 없이 100글자를 의미한다.**

> [MySql 5 : CHAR와 VARCHAR](http://blog.naver.com/PostView.nhn?blogId=ez_&logNo=140117777068)

