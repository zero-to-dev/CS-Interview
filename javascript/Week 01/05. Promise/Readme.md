# Promise 

- 자바스크립트 비동기 처리에 사용되는 객체 (콜백 함수의 단점인 나쁜 가독성, 동시에 여러개의 비동기 처리를 못하는 한계를 보완)
- 서버에서 받아온 데이터를 화면에 표시할 때 사용



- :bookmark: 비동기 처리
    - 특정 코드의 실행이 완료될 때까지 기다리지 않고 다음에 존재하는 코드를 먼저 수행하는 JS의 특성
  
  
<br><br>  
 
# Promise가 필요한 이유

```js
/* 웹 어플리케이션을 구현할 경우 사용하는 API (서버에서 데이터를 요청하고 받아옴) */

$.get('url 주소/products/1', function(response) {
  // ...
});

// API 실행시 서버에 데이터를 보내달라고 request
```


- 데이터를 받아오기 전에 이미 데이터를 다 받아온 것처럼 화면에 데이터를 표시하려고 하는 경우에 오류가 발생 (or 빈 화면으로 등장)<br>=> 이러하 문제점을 해결하는것이 'Promise'


<br><br>

# Promise 생성하기

- Promise는 프로미스 생성자 함수를 통해 인스턴스화 함

- Promise 생성자 함수는 비동기 작업을 수행할 콜백함수를 인자로 전달받는데, 이 콜백 함수는 resolve, reject 함수를 인자로 전달받음

- 프로미스 생성 예시

```js
// Promise 객체의 생성
const promise = new Promise((resolve, reject) => {
  // 비동기 작업을 수행한다.

  if (/* 비동기 작업 수행 성공 */) {
    resolve('result');
  }
  else { /* 비동기 작업 수행 실패 */
    reject('failure reason');
  }
});
```


- 프로미스는 비동기 처리에 대한 상태정보를 가진다

- 프로미스의 상태 정보

|상태 정보|의미|구현하는 시기|
|:--:|:--:|:--:|
|pending|비동기 처리 미수행 상태|resolve / reject 함수가 호출되지 않는 상태|
|fulfilled|비동기 처리를 성공적으로 수행한 상태|resolve 함수가 호출된 상태|
|rejected|비동기 처리를 수행했으나 실패한 상태|reject 함수가 호출된 상태|
|settled|비동기 처리가 수행된 상태(성공/실패)|resolve / reject 함수가 호출된 상태|

