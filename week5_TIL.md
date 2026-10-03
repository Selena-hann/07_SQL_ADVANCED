# SQL_ADVANCED 5주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_5th_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=KZmW6VaY5BU&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=16
https://www.youtube.com/watch?v=vWTDuoSG-YQ&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=17
https://www.youtube.com/watch?v=aiMSluMNzI8&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=18
-->

**교재 실습 예제 파일은 08_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_5th_TIL

### 6장 인덱스
#### 01. 인덱스 개념을 파악하자
#### 02. 인덱스의 내부 작동
#### 03. 인덱스의 실제 사용  


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | ✅         |
| 3주차 | p.158~213  | ✅         |
| 4주차 | p.216~271 | ✅         |
| 5주차 | p.274~327 | ✅         |
| 6주차 | p.330~369 | 🍽️         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 인덱스 개념을 파악하자 

```
- 클러스터형 인덱스: 영어사전처럼 내용이 이미 정렬되어 있는 인덱스. 기본 키로 지정하면 클러스터형 인덱스가 생성되고 해당 열로 자동 정렬됨.
--> 테이블당 개수: 1개
- 보조 인덱스: 일반 책의 찾아보기와 같이 별도의 공간에 인덱스가 생성됨. 고유 키로 지정하면 보조 인덱스가 생성되고 자동 정렬되지 않음.
--> 테이블당 개수: 여러 개
- 고유 인덱스: 값이 중복되지 않는 인덱스. 기본 키나 고유 키로 지정하면 값이 중복되지 않아서 고유 인덱스가 자동 생성됨.
```
> **확인문제: 다음은 인덱스 종류와 관련된 설명입니다. 가장 거리가 먼 것을 하나 고르세요.**

보기는 아래와 같습니다.
```
1️⃣ 클러스터형 인덱스는 영어사전과 비슷한 개념입니다.
2️⃣ 보조 인덱스는 일반 책의 찾아보기와 비슷한 개념입니다.
3️⃣ 클러스터형 인덱스는 기본 키를 설정하면 자동 생성됩니다.
4️⃣ 보조 인덱스는 NOT NULL을 설정하면 자동 생성됩니다.
```

```
4️⃣
보조 인덱스는 고유 키(UNIQUE) 제약 조건을 설정하면 자동으로 생성됨.
NOT NULL은 단순히 열에 빈 값이 들어가지 못하게 막는 제약 조건이라, 인덱스를 만들지 않음.
```


## 2. 인덱스의 내부 작동 

```
- 인덱스는 내부적으로 균형트리, 즉 나무를 거꾸로 표현한 자료 구조로 구성된다.
- 노드는 트리 구조에서 데이터가 저장되는 공간을 말하는데, MySQL에서는 노드를 페이지라고 부른다.
- 전체 테이블 검색은 데이터를 처음부터 끝까지 검색하는 것이다. 인덱스가 없으면 전체 페이지를 검색해야만 한다.
- 페이지 분할은 데이터를 입력할 때, 입력할 페이지에 공간이 없어서 2개 페이지로 데이터가 나눠지는 것을 말한다.
- 인덱스 검색은 클러스터형 또는 보조 인덱스를 이용해서 데이터를 검색하는 것이다. 속도는 인덱스를 사용하지 않았을 때보다 빠르다.
```

> **확인문제: 다음 설명에서 빈칸에 공통으로 들어갈 용어를 쓰시오.**

```
인덱스를 구성하게 되면 데이터의 변경 작업(INSERT, UPDATE, DELETE)시에 성능이 나빠지는 단점이 있습니다.  
특히 INSERT 작업이 일어날 때 더 느리게 입력될 수 있는데요, 이유는 (           ) 이라는 작업이 발생하기 때문입니다.  
(            ) 작업이 일어나면 MySQL이 느려지고 너무 자주 일어나면 성능에 큰 영향을 줍니다.
```

```
페이지 분할
```


## 3. 인덱스의 실제 사용 

<!-- '인덱스 생성과 제거 실습(310p~)' 흐름에 맞게 진행한 후, 실습 과정이 보일 수 있도록 인증 사진을 2장 이상 제출해 주세요. -->

<img width="1136" height="1082" alt="image" src="https://github.com/user-attachments/assets/5f3b459b-4b54-472a-9d18-38111414fbaf" />
<img width="1136" height="1082" alt="image" src="https://github.com/user-attachments/assets/cfef248e-4ca6-4e8e-9300-4f477a47f19d" />



---

# 2️⃣ 실습과제

## 1. 데이터베이스 구축

아래 코드를 MySQL Workbench에 붙여넣은 후,  
**전체 드래그 → 실행 (Ctrl + Shift + Enter)** 하여 데이터베이스를 생성하세요.

```sql
CREATE DATABASE IF NOT EXISTS week5_db;
USE week5_db;

DROP TABLE IF EXISTS employees;

CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(20),
    department VARCHAR(30),
    salary INT,
    hire_date DATE
);

INSERT INTO employees VALUES
(1, '신영', 'Marketing', 3500, '2026-03-01'),
(2, '경모', 'HR', 3200, '2026-06-15'),
(3, '세원', 'IT', 4000, '2024-09-10'),
(4, '진우', 'HR', 5000, '2024-01-20'),
(5, '성환', 'Actuary', 3800, '2025-04-01'),
(6, '혜준', 'Judge', 4500, '2025-12-01'),
(7, '채은', 'HR', 3700, '2026-08-18'),
(8, '다나', 'Actuary', 3700, '2025-08-18');
```

## 2. 실습 문제

다음 문제를 수행하고 실행 결과를 캡처하여 제출하세요.

1. department 컬럼에 보조 인덱스를 생성하시오.
    - 인덱스 생성 후, `SHOW INDEX FROM employees;` 실행 결과가 보이도록 캡처합니다.
    - (idx_department 인덱스가 존재하는지 확인되어야 합니다.)
2. employees 테이블의 인덱스를 확인하시오.
3. department가 'Sales'인 직원을 조회하시오.
   - 'Sales' 조회 시, 반드시 `EXPLAIN`을 함께 실행한 화면을 캡처합니다.
   - (key 컬럼에 idx_department가 표시되어야 합니다.)
4. 생성한 인덱스를 삭제하시오.
   - 인덱스 삭제 후, 다시 `SHOW INDEX FROM employees;`를 실행하여 idx_department가 사라진 것을 확인한 화면을 캡처합니다.

## 3. 제출방법

인덱스 생성 결과, EXPLAIN 실행 결과, 인덱스 삭제 결과가 모두 보이도록 캡처하여 제출하세요.

<img width="1136" height="1082" alt="image" src="https://github.com/user-attachments/assets/d31824d1-251a-47c7-9b0e-9bc4b4e7e18f" />

<img width="1092" height="1038" alt="image" src="https://github.com/user-attachments/assets/323bc0ae-265b-4972-885b-9056f5bface1" />

<img width="1136" height="1082" alt="image" src="https://github.com/user-attachments/assets/45651fd9-7ce0-4444-8b05-9e033b22cb31" />

### 🎉 수고하셨습니다.






