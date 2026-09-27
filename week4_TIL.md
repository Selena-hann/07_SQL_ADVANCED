# SQL_ADVANCED 4주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_4th_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=DMNpkj_bZIs&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=13
https://www.youtube.com/watch?v=BUHj-behLyc&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=14
https://www.youtube.com/watch?v=JrXWxku7ZIM&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=15
-->

**교재 실습 예제 파일은 08_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_4th_TIL

### 5장 테이블과 뷰
#### 01. 테이블 만들기
#### 02. 제약조건으로 테이블을 견고하게
#### 03. SQL 가상의 테이블: 뷰 


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | ✅         |
| 3주차 | p.158~213  | ✅         |
| 4주차 | p.216~271 | ✅         |
| 5주차 | p.274~327 | 🍽️         |
| 6주차 | p.330~369 | 🍽️         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 테이블 만들기 

```
CREATE TABLE 문으로 테이블을 만들며, 테이블 이름과 함께 각 열(컬럼)의 이름, 데이터 타입(예: INT, VARCHAR, DATE 등)을 정의해야한다.
열마다 저장할 데이터의 종류에 맞는 타입을 지정해야 하며, 문자형은 길이(예: VARCHAR(50))를 지정할 수 있다.
```

## 2. 제약조건으로 테이블을 견고하게 

```
제약조건은 테이블에 저장되는 데이터가 일정한 규칙을 지키도록 강제하는 역할을 하며,
이를 통해 데이터의 무결성을 지킬 수 있다.
```

> **확인문제: 다음 보기 중에서 각 문항이 설명하는 것을 고르세요.**

보기는 아래와 같습니다.
```
CHECK / DEFAULT / PRIMAY KEY / UNIQUE / NOT NULL / FOREIGN KEY
```

```
여기에 답과 그 이유를 적어주세요!
1. 입력되는 데이터가 조건에 맞는지 검사하는 기능: CHECK -> 특정 조건(예: 나이>=0)을 만족하는 값만 입력되도록 검사함.
2. 값을 입력하지 않으면 자동으로 들어갈 값: DEFAULT -> 값을 지정하지 않고 INSERT할 경우 미리 정해둔 기본값이 자동으로 채워짐.
3. 빈 값을 입력하는 것을 허용하지 않음: NOT NULL -> 해당 열에 NULL이 들어오는 것을 막아 반드시 값이 있음.
```


## 3. 가상의 테이블: 뷰 

```
뷰(VIEW)는 실제 데이터를 저장하지 않고, 하나 이상의 테이블을 조회하는 SQL문을 저장해두었다가 테이블처럼 사용할 수 있게 해주는 가상의 테이블이다.
복잡한 쿼리를 단순화하고, 특정 열만 보여줌으로써 보안을 강화하는 데도 활용된다.
```

> **확인문제: 다음은 뷰의 특징입니다. 거리가 먼 것을 하나 고르세요.**

보기는 아래와 같습니다.
```
1️⃣ 뷰에는 테이블의 모든 열을 포함시켜야 합니다.
2️⃣ 뷰는 복잡한 SQL을 단순하게 만드는 효과가 있습니다.
3️⃣ 뷰는 보안에 도움이 됩니다.
4️⃣ 일부 사용자가 테이블에는 접근하지 못하게 하고, 뷰에만 접근하도록 설정할 수 있습니다.
```

```
정답: 1️⃣

이유: 뷰는 원본 테이블의 일부 열이나 일부 행만 선택해서 만들 수도 있다.
오히려 보안을 위해 민감한 열(예: 비밀번호, 급여 등)은 제외하고
필요한 열만 포함시켜 뷰를 만드는 경우가 많다.
```


---

# 2️⃣ 실습과제

## 1. 데이터베이스 구축

아래 코드를 MySQL Workbench에 붙여넣은 후,  
**전체 드래그 → 실행 (Ctrl + Shift + Enter)** 하여 데이터베이스를 생성하세요.

```sql
CREATE DATABASE IF NOT EXISTS week4_db;
USE week4_db;
```

## 2. 실습문제

1. 다음 조건을 만족하는 `users` 테이블을 생성하시오.
```
- user_id는 INT이며 **기본키(Primary Key)**로 설정합니다.
- name은 VARCHAR(20)이며 NULL을 허용하지 않습니다.
- email은 VARCHAR(50)이며 중복을 허용하지 않습니다.
- signup_date는 DATE 타입으로 설정합니다.
- grade는 INT이며 기본값(Default)을 1로 설정합니다.
```

<img width="1136" height="1082" alt="image" src="https://github.com/user-attachments/assets/aaf61f4d-b5f4-4b59-945b-e2285e2cbdff" />

2. 다음 조건을 만족하는 `orders` 테이블을 생성하시오.
```
- order_id는 INT이며 기본키(Primary Key)로 설정합니다.
- user_id는 INT이며 NULL을 허용하지 않습니다.
- amount는 INT이며 0보다 커야 합니다.
- order_date는 DATE 타입으로 설정합니다.
```
<img width="1136" height="1082" alt="image" src="https://github.com/user-attachments/assets/18aec473-a8c7-4b19-8cf8-13b0e243fb9e" />

3. 다음 조건을 만족하여 데이터를 삽입하시오.
```
- users 테이블에 3명 이상의 데이터를 직접 INSERT 하시오. (단, user 중 본인이 포함돼야 함)
- orders 테이블에 3건 이상의 데이터를 직접 INSERT 하시오.
```

<img width="1136" height="1082" alt="image" src="https://github.com/user-attachments/assets/f8458dc6-32f9-4ec2-9a71-234867204e1e" />

4. users와 orders 테이블을 활용하여 다음 컬럼을 보여주는 뷰 user_order_view를 생성하시오.
```
- user_id
- name
- amount
```

5. 생성한 user_order_view를 조회하시오.
<img width="1136" height="1082" alt="image" src="https://github.com/user-attachments/assets/7343de85-0b1e-4a4a-855b-adab561309af" />

## 3. 제출 방법

1. 각 문제의 실행 결과가 보이도록 화면을 캡처합니다.
2. 테이블 생성 결과, 데이터 삽입 결과, 뷰 생성 및 조회 결과가 모두 보이도록 제출합니다.

<!-- 이 부분을 지우고 인증사진을 제출해주세요.-->

### 🎉 수고하셨습니다.






