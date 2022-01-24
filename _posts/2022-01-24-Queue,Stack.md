---
title: "자료구조 Queue, Stack"
author: DongWoo Kim
date: 2021-12-22
categories: [SQL]
tags: [SQL, 자료구조, 큐, 스택]
---

---

**자료구조 Queue, Stack**

{:.no_toc}

* Will be replaced with the ToC, excluding the "Contents" header
{:toc}

---

<br/>

# **Stack**
- 스택은 쌓다, 쌓이다 라는 뜻을 가지고 있습니다. 자료구조에서 스택은 말 그대로 아래서부터 위로 쌇는 구조라고 생각하면 됩니다. 맨 마지막에 쌓인 자료를 먼저 가져오는 형태를 띄우고 있습니다.


![placeholer](https://user-images.githubusercontent.com/79832647/150709000-3dafe62c-46b3-43f8-87b7-e807c48fe9c5.jpeg){: .centered}

#### 자바스크립트에서 예시

```js
const stack = []; 

stack.push(1); // [1]
stack.push(2); // [1, 2]
stack.push(3); // [1, 2, 3]
stack.push(4); // [1, 2, 3, 4]
stack.push(5); // [1, 2, 3, 4, 5]

console.log(stack); // [1, 2, 3, 4, 5]

stack.pop(); // [1, 2, 3, 4]
stack.pop(); // [1, 2, 3]

console.log(stack); // [1, 2, 3]
```

<br />

# **Queue**
- 큐는 줄을 서서 기다리다, 대기 행렬 이라는 뜻을 가지고 있다. 자료구조 큐는 스택과 반대되는 개념으로 먼저 들어간 FIFO(First In First Out) 혹은 LILO(Last In Last Out) 을 특징으로 가지고 있습니다. 티켓을 사려고 줄을 서서 기다리는 모습과 흡사한 구조를 가지고 있습니다.


![placeholer](https://user-images.githubusercontent.com/79832647/150709006-02645881-55ea-4c3e-9145-cd836920d285.jpeg){: .centered}


#### 자바스크립트에서의 예시

```js
const queue = []; 

queue.push(1); // [1]
queue.push(2); // [1, 2]
queue.push(3); // [1, 2, 3]
queue.push(4); // [1, 2, 3, 4]
queue.push(5); // [1, 2, 3, 4, 5]

console.log(queue); // [1, 2, 3, 4, 5]

queue.shift(); // [2, 3, 4, 5]
queue.shift(); // [3, 4, 5]

console.log(queue); // [3, 4, 5]
```