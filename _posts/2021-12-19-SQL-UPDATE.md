---
title: "SQL 기본 문법 - UPDATE "
author: DongWoo Kim
date: 2021-12-11
categories: [SQL]
tags: [SQL, 기본문법, UPDATE]
---

---

**SQL 기초 문법**

{:.no_toc}

* Will be replaced with the ToC, excluding the "Contents" header
{:toc}
---


<br/>

# **UPDATE**
- UPDATE 문법을 사용하여 레코드의 내용을 수정 할 수 있습니다.

__예시__
```sql
UPDATE 테이블이름
SET 필드이름1 = 데이터값1, 필드이름2 = 데이터값2, ....
WHERE 필드이름=데이터값
```

- UPDATE 문법은 해당 테이블에서 WHERE 절의 조건을 만족하는 레코드값만 수정합니다.

__예제__
- Test 테이블에서 Name 필드의 값이 'kdw'인 모든 레코드의 RoomName 값을 1803으로 변경하는 예제입니다.

```sql
UPDATE Test
SET RoomName = 1803
WHERE Name = 'kdw'
```

__만약 WHERE 절을 생략하면 해당 테이블의 모든 레코드의 RoomName 값이 1803으로 변경됩니다.__