---
title: "SQL 기본 문법 - SELECT "
author: DongWoo Kim
date: 2021-12-11
categories: [SQL]
tags: [SQL, 기본문법, SELECT]
---

---

**SQL 기초 문법**

{:.no_toc}

* Will be replaced with the ToC, excluding the "Contents" header
{:toc}
---


<br/>

# **SELECT**
- SELECT 문법을 사용하여 테이블의 레코드를 선택할 수 있습니다.

__예시__
```sql
SELECT 필드이름
FROM 테이블이름
WHERE 조건
```

- FROM 절은 레코드를 선택할 테이블의 이름을 명시합니다.
- WHERE 절을 사용하면 선택할 레코드의 조건을 상세하게 설정할 수 있습니다.


# **테이블의 모든 필드 선택**
- SELECT 문법과 함께 ``*`` 기호를 사용하면 해당 테이블의 모든 필드를 선택할 수 있습니다.

__예시__
```sql
SELECT *
FROM 테이블이름
```

__예제__
- Test의 모든 핋드를 선택하는 예제입니다.

```sql
SELECT * FROM Test;
```

<br/>

# **특정 조건의 레코드 선택**
- SELECT 문법과 WHERE 절을 사용하면 검색할 레코드의 특정조건을 설정할 수 있습니다.

__예제__
- Name 필드의 값이 'kdw'인 레코드만을 선택하는 예제입니다.

```sql
SELECT * 
FROM Test
WHERE Name = 'kdw'
```



# **특정 필드만 선택**
- SELECT 문법 다음에 필드 이름을 명시하면 해당 테이블의 특정 필드만을 불러 올 수 있습니다.
- ```,``` 쉼표를 사용하여 여러개의 필드 이름을 선택 할 수 있습니다.

__예제__
- Test 테이블에서 Name 필드와 Phone 필드만 선택하는 예제입니다.

```sql
SELECT Name, Phone
FROM test;
```


# **중복되는 값 제거**
- 같은 필드에서 중복된 값을 가지는 레코드가 있으면 DISTINCT 문법을 사용하여 그 값의 한번만 선택되도록 설정 할 수 있습니다.

__예제__
- Test 테이블에서 Name 필드를 선택하는 예제입니다.

```sql
SELECT DISTINCT Name
From Test
```

