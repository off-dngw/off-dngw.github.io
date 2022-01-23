---
title: "SQL 기본 문법 - INSERT "
author: DongWoo Kim
date: 2021-12-11
categories: [SQL]
tags: [SQL, 기본문법, INSERT]
---

---

**SQL 기초 문법**

{:.no_toc}

* Will be replaced with the ToC, excluding the "Contents" header
{:toc}
---


<br/>

# **INSERT**
- INSERT INTO 문법을 사용하여 테이블에 새로운 레코드를 추가할 수 있습니다.

# **테이블에 레코드 추가**
- INSERT INTO 문법과 함께 VALUES절을 사용하여 해당 테이블에 새로운 레코드를 추가할 수 있습니다.

__예시__

```sql
1. INSERT INTO 테이블이름(필드이름1, 필드이름2, ...)
   VALUES (데이터값1, 데이터값2, ...)

2. INSERT INTO 테이블이름
   VALUES (데이터값1, 데이터값2, ...)
```

__두 번째 문법처럼 필드의 이름을 생략할 수 있습니다. 이 경우에는 데이터베이스 스키마와 같은 순서대로 필드의 값이 자동으로 대입됩니다. 이때 생략 할 수 있는 필드는 다음과 같습니다.__

1. DEFAULT 제약 조건이 설정된 필드
2. NULL을 저장할 수 있도록 설정된 필드
3. AUTO_INCREMENT 키워드가 설정된 필드


__예제__
- Test 테이블에 새로운 레코드를 추가하는 예제입니다.

```sql
INSERT INTO Test (ID, Name)
VALUES(2, 'lee');
```

