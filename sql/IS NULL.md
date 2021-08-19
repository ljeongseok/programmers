# IS NULL

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

## 이름이 없는 동물의 아이디

**Level1**

동물 보호소에 들어온 동물 중, 이름이 없는 채로 들어온 동물의 ID를 조회하는 SQL 문을 작성해주세요. 단, ID는 오름차순 정렬되어야 합니다.

**입출력 예**

| ANIMAL_ID |
| --------- |
| A368930   |

**코드*

```mysql
SELECT animal_id
from animal_ins
where name is null
order by name
```

## 이름이 있는 동물의 아이디

**Level1**

동물 보호소에 들어온 동물 중, 이름이 있는 동물의 ID를 조회하는 SQL 문을 작성해주세요. 단, ID는 오름차순 정렬되어야 합니다.

**입출력 예**

| ANIMAL_ID |
| --------- |
| A465637   |
| A524634   |

**코드**

```sql
SELECT ANIMAL_ID
from animal_ins
where name is not null
order by animal_id
```

## NULL 처리하기

**Level2**

입양 게시판에 동물 정보를 게시하려 합니다. 동물의 생물 종, 이름, 성별 및 중성화 여부를 아이디 순으로 조회하는 SQL문을 작성해주세요. 이때 프로그래밍을 모르는 사람들은 NULL이라는 기호를 모르기 때문에, 이름이 없는 동물의 이름은 "No name"으로 표시해 주세요.

**입출력 예**

마지막 줄의 개는 이름이 없기 때문에, 이 개의 이름은 "No name"으로 표시합니다. 따라서 SQL문을 실행하면 다음과 같이 나와야 합니다.

| ANIMAL_TYPE | NAME    | SEX_UPON_INTAKE |
| ----------- | ------- | --------------- |
| Cat         | Jewel   | Spayed Female   |
| Cat         | Meo     | Neutered Male   |
| Dog         | No name | Spayed Female   |

**코드**

```sql
SELECT ANIMAL_TYPE, if (name is null,'No name',name) as 'NAME', SEX_UPON_INTAKE
from animal_ins
order by animal_id
```



> 출처 : 프로그래머스 코딩테스트 연습  https://programmers.co.kr/learn/courses/30/parts/17043

