---
title: "SQL 기본 문법 - DELETE "
author: DongWoo Kim
date: 2021-12-11
categories: [SQL]
tags: [SQL, 기본문법, DELETE]
---

---

**SQL 기초 문법**

{:.no_toc}

* Will be replaced with the ToC, excluding the "Contents" header
{:toc}
---


<br/>

# **DELETE**
- DELETE 문법을 사용하여 테이블의 레코드값을 삭제 할 수 있습니다.

__예시__

```sql
DELETE FROM 테이블이름
WHERE 필드이름 = 데이터값
```

- DELETE 문법은 WHERE 절의 조건을 만족하는 레코드값을 삭제합니다
- __만약 WHERE절을 생략하면 해당 테이블에 저장된 모든 데이터가 삭제 됩니다.__

__예시__
```sql
DELETE FROM 테이블 이름
```

- 테이블에 저장된 모든 데이터가 삭제되어도 테이블은 여전히 남아 있기 때문에 해당 테이블 까지 삭제 하고 싶을 때는 DROP TABLE 문법을 사용하면 됩니다.


__예제__
- Test 테이블에서 Name 필드의 값이 'kdw'인 모든 레코드를 삭제하는 예제입니다.

```sql
DELETE FROM Test
WHERE Name = 'kdw'
```

