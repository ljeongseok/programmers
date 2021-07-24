# SUM,MAX,MIN

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



## 최댓값 구하기

**Level 1**

가장 최근에 들어온 동물은 언제 들어왔는지 조회하는 SQL 문을 작성해주세요.

**입출력 예**

가장 늦게 들어온 동물은 Anna이고, Anna는 2013-11-18 17:03:00에 들어왔습니다. 따라서 SQL문을 실행하면 다음과 같이 나와야 합니다.

| 시간                |
| ------------------- |
| 2013-11-18 17:03:00 |

**코드**

```mysql
SELECT datetime as "시간"
from animal_ins
order by datetime desc limit 1
```

## 최솟값 구하기

**Level 2**

동물 보호소에 가장 먼저 들어온 동물은 언제 들어왔는지 조회하는 SQL 문을 작성해주세요.

**입출력 예**

가장 먼저 들어온 동물은 Jack이고, Jack은 2013-10-14 15:38:00에 들어왔습니다. 따라서 SQL문을 실행하면 다음과 같이 나와야 합니다.

| 시간                |
| ------------------- |
| 2013-10-14 15:38:00 |

**코드**

```mysql
SELECT min(datetime) as '시간'
from animal_ins
```



## 동물 수 구하기

**Level 2**

동물 보호소에 동물이 몇 마리 들어왔는지 조회하는 SQL 문을 작성해주세요.

**입출력 예**

동물 보호소에 들어온 동물은 4마리입니다. 따라서 SQL문을 실행하면 다음과 같이 나와야 합니다.

| count |
| ----- |
| 4     |

**코드**

```mysql
SELECT count(*) 'count'
from animal_ins
```

## 중복 제거하기

**Level 2**

동물 보호소에 들어온 동물의 이름은 몇 개인지 조회하는 SQL 문을 작성해주세요. 이때 이름이 NULL인 경우는 집계하지 않으며 중복되는 이름은 하나로 칩니다.

**입출력 예**

보호소에 들어온 동물의 이름은 NULL(없음), `*Sam`, `*Sam`, `*Sweetie`입니다. 이 중 NULL과 중복되는 이름을 고려하면, 보호소에 들어온 동물 이름의 수는 2입니다. 따라서 SQL문을 실행하면 다음과 같이 나와야 합니다.

| count |
| ----- |
| 2     |

**코드**

```mysql
SELECT count(distinct name) "count"
from animal_ins
```



> 출처 : 프로그래머스 코딩테스트 연습  https://programmers.co.kr/learn/courses/30/parts/17043

