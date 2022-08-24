# this

- 자바스크립트의 함수는 호출될 때, 매개변수로 전달되는 인자값 외에 arguments 객체와 this를 암묵적으로 전달받음


```js

function func1(){
    console.log("func1 is called")
    console.log("this 수행: ",this);
}
// this-> 예약어. 함수가 불렸을 때, 어떤 객체에 bind된 속성으로서 불렸는지를 알 수 있게 해줌
// 우리는 브라우저에서 실행하고 있으므로 가장 바깥인 전역에 선언한 함수들은 모두 window라는 브라우저에 bind됨
// 따라서 func1()함수 호출시 ->  window 객체가 출력됨
// 객체의 메서드로 호출시 -> Object가 출력됨

function setName(name){
    this.name = name;
}


var obj1 = {name: "object1", method: func1, setName: setName};   // 함수가 객체의 속성이 될 경우 '메서드'라고 부름
var obj2 = {name: "", setName:setName};

/*
func1();   // 함수를 바로 호출 -> func1 is called
console.log();
obj1.method();   // 객체의 속성에 bind된 함수로서 호출 -> func1 is called
*/

obj1.setName("object1");
obj2.setName("object2");

console.log("obj1:",obj1);  // name이 object1로 변경
console.log();
console.log("obj2:",obj2);   // name이 object2로 변경

// 두 객체의 속성으로 저장된 setName메서드가 각각 호출되었을 때 this 키워드가 obj1, obj2의 객체의 이름을 변경함
// 이처럼 함수를 객체의 속성(메서드)로 저장해두고 호출시, 함수 내에서 어떤 객체가  함수를 호출하였는지 this라는 키워드를 통해 접근할 수 있음
```
