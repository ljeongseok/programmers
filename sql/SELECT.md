# SELECT

## 모든 레코드 조회하기 (level1)

동물 보호소에 들어온 모든 동물의 정보를 ANIMAL_ID순으로 조회하는 SQL문을 작성

```mysql
SELECT *
from animal_ins
order by Animal_id
```

## 역순 정렬하기

동물 보호소에 들어온 모든 동물의 이름과 보호 시작일을 조회하는 SQL문을 작성해주세요. 이때 결과는 ANIMAL_ID 역순으로 보여주세요.

```mysql
SELECT name, datetime
from animal_ins
order by animal_id desc
```

## 

> 출처 : 프로그래머스 코딩 테스트 연습  https://programmers.co.kr/learn/challenges

