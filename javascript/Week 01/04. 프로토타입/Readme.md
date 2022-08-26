# Prototype (프로토타입) 

- Javascript는 프로토타입 기반 객체지향 프로그래밍 언어이다

<br>

- 객체지향 프로그래밍 언어 비교
|클래스 기반 객체지향 프로그래밍 언어|프로토타입 기반 객체지향 프로그래밍 언어|
|:--:|:--:|
|Java, C++|Javascript|
|객체 생성 이전에 클래스를 정의하고 이를 통해 객체(인스턴스)를 생성)|클래스 없이 객체 생성|


- JS의 모든 객체는 부모 역할을 하는 객체와 연결되어있는데, 이러한 부모 객체를 <b>Prototype 객체</b>라 한다 (= Prototype)

- 프로토타입 객체는 생성자 함수에 의해 생성된 각각의 객체에 공유 프로퍼티를 제공하기 위해 사용함


- 예시
```js
var student = {
  name: 'KIM',
  score: 85
};

// student에는 hasOwnProperty 메소드가 없지만 아래 구문은 동작함
console.log(student.hasOwnProperty('name')); // true

console.dir(student);

```


- student 객체 Output
![image](https://user-images.githubusercontent.com/68424403/186930612-ce1cdfb2-effe-4490-bb62-d79d2799d0b1.png)

<br>

- 객체 생성시 프로토타입이 결정됨
- 결정된 프로토타입 객체는 다른 임의의 객체로 변경이 가능함 (동적인 변경 가능)
- 변경 가능하다는 특징을 이용하여 객체의 상속 구현 가능

