---
layout: post
title: MySQL - table(crud)
category: MySql
tags: [MySql, 데이터베이스]
comments: true
---

## 테이블
실질적으로 데이터가 저장되는 장소


## 생성
```shell
#문법
CREATE TABLE 테이블명 (컬럼명 데이터타입(크기) 그외옵션);

#예제
CREATE TABLE person(
ID   CHAR(12) NOT NULL AUTO_INCREMENT PRIMERY KEY,
NAME VARCHAR(10) NOT NULL,
AGE  INT(10) NOT NULL DEFAULT 10
);
```

```shell
#옵션
NOT NULL: 반드시 입력해야 하는 필드
AUTO_INCREMENT: 자동으로 1씩 증가하는 필드
PRIMARY KEY: 기본키(테이블에서의 고유값이며 NULL을 허용하지 않음)
DEFAULT: 기본값 설정
UNIQUE: PRIMERY KEY와 같이 중복을 허용하지 않는 고유값이지만 NULL을 허용한다.
FOREIGN KEY : 다른 테이블을 참조하는 키. 즉 다른 테이블에서 가져온 값 
```

## 조회
- 전체 테이블 목록 조회
```shell
SHOW TABLES;
```
- 특정 테이블 구조 조회(describe)
```shell
DESC 테이블명;
```


## 수정
- 테이블에 필드 추가
```shell
#문법
ALTER TABLE 테이블명 ADD 컬럼명 자료형;
#예제
ALTER TABLE person ADD phone_number VARCHAR(15);
```

- 테이블 필드의 자료형 수정
```shell
#문법 
ALTER TABLE 테이블명 MODIFY 컬럼명 자료형;
#예제 
ALTER TABLE person MODIFY COLUMN age CHAR(3);
```

- 테이블 필드명을 변경
```shell
#문법
ALTER TABLE 테이블명 CHANGE COLUMN 컬럼명;
#예제
ALTER TABLE person CHANGE COLUMN phone_number number; 
```

## 삭제 
- 테이블 삭제
```shell
DROP TABLE 테이블명;
```
- 테이블 내의 데이터 모두 삭제
```shell
TRUNCATE TABLE 테이블명;
```



