# SQL_ADVANCED 2주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_2nd_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=_JURyg_KzHE&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=7
https://www.youtube.com/watch?v=6qkPy7RfLqQ&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=8
https://www.youtube.com/watch?v=WWAFAm9op2U&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=9
-->

**교재 실습 예제 파일은 08_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_2nd_TIL

### 3장 SQL 기본 문법
#### 01. 기본 중에 기본 SELECT ~ FROM ~ WHERE
#### 02. 좀 더 깊게 알아보는 SELECT문
#### 03. 데이터 변경을 위한 SQL문


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | ✅         |
| 3주차 | p.158~213  | 🍽️         |
| 4주차 | p.216~271 | 🍽️         |
| 5주차 | p.274~327 | 🍽️         |
| 6주차 | p.330~369 | 🍽️         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 기본 중에 기본 SELECT ~ FROM ~ WHERE

<!-- 기본적인 SQL 문법에 관해 배우게 된 점을 적어주세요. -->

<!-- 과제 페이지를 참조하여 인증 사진 2장을 아래의 부분을 지우고 제출해주세요. -->

<img width="1136" height="1082" alt="image" src="https://github.com/user-attachments/assets/facb2475-e20c-42b4-9b3c-11f80b294a25" />
<img width="1136" height="1082" alt="image" src="https://github.com/user-attachments/assets/e5d102ab-7af4-4974-9b90-691cf8de99c6" />


> **확인문제: 주소의 지역이 서울, 경기인 회원을 추출하는 SQL 문입니다. 빈칸에 들어갈 수 있는 것을 모두 고르세요.**

```sql
SELECT *
FROM table
WHERE ________;
```

보기는 아래와 같습니다.
```
1. addr IN('서울', '경기')
2. addr BETWEEN '서울' AND '경기'
3. addr = '서울' OR addr = '경기'
4. addr = '서울' AND addr = '경기'
```

```
1,3
IN은 지정한 값들 중 하나와 일치하는 행을 찾으므로 서울 또는 경기인 회원을 추출한다.
OR로 연결된 것은 IN을 풀어쓴 것과 동일한 표현으로 주소가 서울 또는 경기인 행을 모두 찾는다.

```


## 2. 좀 더 깊게 알아보는 SELECT문

<!-- ORDER BY절과 GROUP BY절 그리고 HAVING절에 관해 배우게 된 점을 적어주세요. -->

```
여기에 배우게 된 점을 적어주세요!
ORDER BY절: 조회 결과를 특정 컬럼 기준으로 정렬할 때 사용한다. 기본값은 오름차순이며, SELECT 문의 가장 마지막에 위치한다.
GROUP BY절: 특정 컬럼의 값이 같은 행들을 하나의 그룹으로 묶어준다. 주로 SUM, AVG, COUNT 같은 집계함수와 함께 사용하며 그룹별 통계를 구할 때 쓴다.
HAVING절: GROUP BY로 묶인 그룹에 대해 조건을 걸 때 사용한다. 그룹으로 묶은 후 집계 결과에 대해 조건을 건다. 그래서 집계함수 SUM, COUNT 등을 조건식에 사용할 수 있다.
```

> **확인문제: 다음 표는 주요 집계함수를 정리한 것입니다. 각 설명에 해당하는 올바른 함수명을 기호에 맞게 작성하세요.**

| 함수명 | 설명 |
|--------|------|
| SUM() | 합계를 구합니다. |
| (ㄱ) | 평균을 구합니다. |
| (ㄴ) | 최소값을 구합니다. |
| MAX() | 최대값을 구합니다. |
| (ㄷ) | 행의 개수를 셉니다. |
| (ㄹ) | 행의 개수를 셉니다 (중복은 1개만 인정). |

```
여기에 답을 적어주세요!
(ㄱ) AVG()
(ㄴ) MUN()
(ㄷ) COUNT(*)
(ㄹ) COUNT(DISTINCT 컬럼명)
```


## 3. 데이터 변경을 위한 SQL문

<!-- INSERT문, UPDATE문, DELETE문에 관해 배우게 된 점을 적어주세요. -->

```
여기에 배우게 된 점을 적어주세요!
INSERT문: 테이블에 데이터를 입력하는 명령이다.
UPDATE문: 기존에 입력되어 있는 값을 수정하며 주로 WHERE과 함께 사용한다.
DELETE문: 행 단위로 삭제하며 WHERE이 없으면 전체 행이 삭제된다.
```


# 2️⃣ 실습과제

다음 SQL 문을 작성하고 실행 결과를 확인 후 인증 사진을 아래에 업로드하세요.(market_db를 그대로 사용합니다.)

1. 모든 그룹 멤버의 정보를 조회하시오.
2. 멤버의 수가 6명 이상인 그룹 정보를 조회하시오.
3. 현재 구매 테이블에 존재하는 서로 다른 상품(prod_name)이 어떤 것이 있는지 조회하시오.
4. 총 구매 금액이 1000미만인 prod_name 중 상위 2개만 조회하시오.

<img width="1136" height="1082" alt="image" src="https://github.com/user-attachments/assets/33422908-f0d3-4bc7-aece-74d79cd9b1c4" />


### 🎉 수고하셨습니다.






