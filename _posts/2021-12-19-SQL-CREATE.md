---
title: "SQL 기본 문법 - CREATE "
author: DongWoo Kim
date: 2021-12-11
categories: [SQL]
tags: [SQL, 기본문법, CREATE]
---

---

**SQL 기초 문법**

{:.no_toc}

* Will be replaced with the ToC, excluding the "Contents" header
{:toc}
---


<br/>

# **CREATE**
- CREATE 문법을 사용하여 데이터베이스와 테이블을 생성할 수 있습니다.

#### 1. 데이터 베이스 생성

```CREATE DATABASE 데이터베이스이름```

```sql
CREATE DATABASE Test;
```

<br />

<br />



#### 2. 테이블 생성
- 데이터 베이스는 하나 이상의 테이블로 구성이 됩니다.
- 테이블에 데이터를 저장하여 관리를 할 수가 있으며 CREATE TABLE 문법을 사용해 테이블을 생성할 수 있습니다.

__예시__

```
CREATE TABLE 테이블이름(
    필드이름, 필드타입,
    필드이름1, 필트타입1
)
```

__예제__
```sql
CREATE TABLE Test(
    ID INT,
    NAME VARCHAR(255);
)
```