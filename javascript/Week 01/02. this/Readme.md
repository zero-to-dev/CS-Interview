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


<br><br>

```js
/* javascript - this */
// 대부분의 경우, this의 값은 함수를 호출하는 방법에 의해 결정됨 (중요)
// 자바스크립트에서는 1) 선언할 때 결정되는 것(클로저 - 선언되는 위치에 따라 달라짐) 2) 호출할 때 결정되는 것 (this- 호출하는 방법에 의해 결정 )이 존재
// this - 실행하는 동안의 할당에 의해 설정될 수 없고, 함수가 다를 수 있음
// ES5 에서는 bind를 가지고 호출되는 방법에 따라 달라지지 않고 고정시킬 수 있음

var someone ={
    name: 'codejong',
    whoAmI: function(){
        console.log(this);   // 자기 자신을 콘솔에 찍음
    }
};

someone.whoAmI(); //  { name: 'codejong', whoAmI: [Function: whoAmI] }
// 여기서 whoAmI를 직접호출한 애는 someone임 (.이 중요)



// 호출하는 방법을 다르게 설정
var myWhoAmI = someone.whoAmI;
myWhoAmI();   // someone의 myWhoAmI와 동일 BUT 출력결과는 다름 -> window가 등장
// myWhoAmI가 global에 존재하고, global은 window객체임. 따라서 window가 호출한 셈임 (브라우저가 윈도우임)



/* */

var btn1 = document.getElementById('btn1');
btn1.addEventListener('click', someone.whoAmI);





// 핵심=> 호출한 놈(객체) === this
// js는 누가 실행했느냐가 핵심. 그 '누가'가 바로 'this'임
// this를 고정시키는 애가 bind임

var bindedWhoAmI = myWhoAmI.bind(someone);   // bind는 someone을 this로 고정시키겠다는 것
// bind에 의해 묶인 애가 무조건 this임

// this는 호출할 때 결정됨
// this는 호출한 객체임
// this를 예외적으로 호출과 무관하게 묶어주는 애가 bind라는 함수임
// 
```



<br><br>

# this 

```js
/* this */
// 함수 호출 맥락(context)를 뜻함
// 맥락 - 같은 상황에 따라서 달라진다는 뜻.
// 즉, 함수를 어떻게 호출하느냐에 따라서 this가 가리키는 대상이 달라진다는 뜻
// 함수와 객체의 느슨한 관계가 느슨한 자바스크립트에서 this는 이 둘을 연결시켜주는 실질적인 연결점 역할을 함

// this -> 함수 내에서 사용할 수 있는 일종의 변수이며, 약속된 변수. 변수 내에 담겨있는 값은 그 함수를 어떻게 호출하느냐에 따라 달라짐

/* this 예시1 */
function func1(){
    if (window === this){
        // window - client javascript. 웹 브라우저 자바스크립트에서 전역객체의 이름
        // function 내에서 this 변수와 같은지를 체크
        console.log("window === this");
    }
}

func1(); 
```


