# GROUP BY

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



## 고양이와 개는 몇 마리 있을까

**Level 2**

동물 보호소에 들어온 동물 중 고양이와 개가 각각 몇 마리인지 조회하는 SQL문을 작성해주세요. 이때 고양이를 개보다 먼저 조회해주세요.

**입출력 예**

고양이는 2마리, 개는 1마리 들어왔습니다. 따라서 SQL문을 실행하면 다음과 같이 나와야 합니다.

| ANIMAL_TYPE | count |
| ----------- | ----- |
| Cat         | 2     |
| Dog         | 1     |

**코드**

```mysql
SELECT ANIMAL_TYPE, count(datetime) as "count"
from animal_ins
group by animal_type
order by animal_type
```

## 동명 동물 수 찾기

**Level 2**

동물 보호소에 들어온 동물 이름 중 두 번 이상 쓰인 이름과 해당 이름이 쓰인 횟수를 조회하는 SQL문을 작성해주세요. 이때 결과는 이름이 없는 동물은 집계에서 제외하며, 결과는 이름 순으로 조회해주세요.

**입출력 예**

- Raven 이름은 2번 쓰였습니다.
- Lucy 이름은 3번 쓰였습니다
- Shadow 이름은 1번 쓰였습니다.

따라서 SQL문을 실행하면 다음과 같이 나와야 합니다.

| NAME  | COUNT |
| ----- | ----- |
| Lucy  | 3     |
| Raven | 2     |

**코드**

```mysql
SELECT name, count(name)
from animal_ins
group by name
having count(name) >1
order by name
```



## 입양 시각 구하기(1)

**Level 2**

보호소에서는 몇 시에 입양이 가장 활발하게 일어나는지 알아보려 합니다. 09:00부터 19:59까지, 각 시간대별로 입양이 몇 건이나 발생했는지 조회하는 SQL문을 작성해주세요. 이때 결과는 시간대 순으로 정렬해야 합니다.

##### 입출력 예

SQL문을 실행하면 다음과 같이 나와야 합니다.

| HOUR | COUNT |
| ---- | ----- |
| 9    | 1     |
| 10   | 2     |
| 11   | 13    |
| 12   | 10    |
| 13   | 14    |
| 14   | 9     |
| 15   | 7     |
| 16   | 10    |
| 17   | 12    |
| 18   | 16    |
| 19   | 2     |

**코드**

```mysql
SELECT hour(datetime) "HOUR" , count(hour(datetime)) "COUNT"
from animal_outs
group by hour(datetime)
having hour between 9 and 19
order by hour(datetime)
```

