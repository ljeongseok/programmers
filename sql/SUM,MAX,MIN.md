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



## 문제

### 최댓값 구하기

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

### 동물 수 구하기

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

