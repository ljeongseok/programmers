# SELECT

## 데이터

`ANIMAL_INS` 테이블은 동물 보호소에 들어온 동물의 정보를 담은 테이블입니다. `ANIMAL_INS` 테이블 구조는 다음과 같으며, `ANIMAL_ID`, `ANIMAL_TYPE`, `DATETIME`, `INTAKE_CONDITION`, `NAME`, `SEX_UPON_INTAKE`는 각각 동물의 아이디, 생물 종, 보호 시작일, 보호 시작 시 상태, 이름, 성별 및 중성화 여부를 나타냅니다.

| NAME             | TYPE       | NULLABLE |
| ---------------- | ---------- | -------- |
| ANIMAL_ID        | VARCHAR(N) | FALSE    |
| ANIMAL_TYPE      | VARCHAR(N) | FALSE    |
| DATETIME         | DATETIME   | FALSE    |
| INTAKE_CONDITION | VARCHAR(N) | FALSE    |
| NAME             | VARCHAR(N) | TRUE     |
| SEX_UPON_INTAKE  | VARCHAR(N) | FALSE    |



## 모든 레코드 조회하기 

**Level 1**

동물 보호소에 들어온 모든 동물의 정보를 ANIMAL_ID순으로 조회하는 SQL문을 작성

```mysql
SELECT *
from animal_ins
order by Animal_id
```

## 역순 정렬하기

**Level 1**

동물 보호소에 들어온 모든 동물의 이름과 보호 시작일을 조회하는 SQL문을 작성해주세요. 이때 결과는 ANIMAL_ID 역순으로 보여주세요.

```mysql
SELECT name, datetime
from animal_ins
order by animal_id desc
```



## 아픈 동물 찾기

**Level 1**

동물 보호소에 들어온 동물 중 아픈 동물(`INTAKE_CONDITION = Sick`)의 아이디와 이름을 조회하는 SQL 문을 작성해주세요. 이때 결과는 아이디 순으로 조회해주세요.

**입출력 예**

| ANIMAL_ID | NAME     |
| --------- | -------- |
| A367012   | Miller   |
| A381217   | Cherokee |

**코드**

```mysql
SELECT animal_id,name
from animal_ins
where intake_condition = "sick"
order by animal_id
```

## 어린 동물 찾기

**Level 1**

동물 보호소에 들어온 동물 중 젊은 동물의 아이디와 이름을 조회하는 SQL 문을 작성해주세요. 이때 결과는 아이디 순으로 조회해주세요.

젊은 동물은 `INTAKE_CONDITION`이 Aged가 아닌 경우를 뜻함

**입출력 예**

| ANIMAL_ID | NAME     |
| --------- | -------- |
| A365172   | Diablo   |
| A367012   | Miller   |
| A381217   | Cherokee |

**코드**

```mysql
SELECT animal_id,name
from animal_ins
where intake_condition != "Aged"
order by animal_id
```

## 동물의 아이디와 이름

**Level1**

동물 보호소에 들어온 모든 동물의 아이디와 이름을 ANIMAL_ID순으로 조회하는 SQL문을 작성해주세요.

**입출력 예**

| ANIMAL_ID | NAME         |
| --------- | ------------ |
| A349996   | Sugar        |
| A350276   | Jewel        |
| A350375   | Meo          |
| A352555   | Harley       |
| A352713   | Gia          |
| A352872   | Peanutbutter |
| A353259   | Bj           |

**코드**

```mysql
SELECT animal_id, name
from animal_ins
order by animal_id
```



## 상위 n개 레코드

__Level1__

동물 보호소에 가장 먼저 들어온 동물의 이름을 조회하는 SQL 문을 작성해주세요.

##### **입출력 예**

| NAME |
| ---- |
| Jack |

**코드**

```mysql
SELECT NAME
from animal_ins
order by datetime limit 1
```



> 출처 : 프로그래머스 코딩 테스트 연습  https://programmers.co.kr/learn/challenges

