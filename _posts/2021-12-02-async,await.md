---
title: async & await
author: DongWoo Kim
date: 2021-12-03 10:00:00
categories: [JS, 기초문법]
tags: [JS, Promise]
---

---

**async & await**

{:.no_toc}

* Will be replaced with the ToC, excluding the "Contents" header
{:toc}
---

<br/>

# **async & await**
- async & await 은 자바스크립트 비동기 처리 패턴중 가장 최근에 나온 문법입니다.
- 기존에 비동기 처리 방식인 콜백 함수와 프로미스의 단점을 보완하고 개발자가 읽기 좋은 코드로 작성할 수 있게 도와 줍니다.


<br/>

---


# **async & await 기본문법**
```js
async function 함수이름(){
    await 비동기 처리 메소드 이름()
}

```

<br/>

- 함수 앞에 async라는 예약어를 붙입니다.
- 함수의 내부 로직중 HTTP 통신을 하는 비동기 처리 코드 앞에 await을 붙입니다.
- 비동기 처리 메소드가 꼭 프로미스 객체를 반환해야 await이 의도한 대로 동작합니다.


<br/>



---


# **async & await 예제**

- 앞에서 학습한 Promise 예제코드를 async 함수로 바꿔 작성해 보겠습니다.


```js
function doJob(name, person){
    return new Promise(resolve, reject) => {
        setTimeout(() =>{
            if(person.hp > 50){
                resolve({
                    result : `${name} success`,
                    loss : 30
                })
            }else{
                reject(new Error(`${name} failed`))
            }
        }, 1000)
    }
}

const kim = {hp : 100}

const execute = async function(){

    try{
        let v = await doJob('work', kim)
        console.log(v.result)
        v = await doJob('study', kim)
        console.log(v.result)
        v = await doJob('work', kim)
        console.log(v.result)
        v = await doJob('study', kim)
        console.log(v.result)
    }catch(e){
        console.log(v)
    }
}

execute()
```

<br/>

18 코드설명 <br/>
- 표현식 익명함수 function 앞에 async를 추가하여 execute 함수 내부에 비동기 작업을 제어합니다.

19 ~ 30 코드설명 <br/>
- 비동기로 처리되는 doJob 함수를 연달아 호출합니다.
- 비동기 로직 앞에 await을 추가하면 비동기 작업이 끝날 때까지 기다렸다가 다음 코드를 처리합니다.

20 ~ 23 코드설명 <br/>
- hp값이 50 이상이기 때문에 1초 간격으로 에러 없이 처리 됩니다.

24 코드설명 <br/>
- hp값이 50이하기 때문에 new Error work failed 에러를 반환합니다.

27 ~ 29 코드설명 <br/>
- 에러 발생시 try-catch 메소드를 통해 전달한 함수가 호출되어 거절된 이유인 에러 객체가 콘솔에 에러로 출력이 됩니다.


