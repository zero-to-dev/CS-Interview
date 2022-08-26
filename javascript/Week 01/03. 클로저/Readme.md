# 클로저

##

```js
// closure - 고급 자바스크립트 개발자가 되기 위해 매우 중요한 개념
// 자바스크립트의 함수와 함수의 environment로 구성
function makeCounterFunction(iniVal){
    var count = iniVal;
    function Increase(){   // 함수 선언
        count++;
        console.log(count);
    }
    return Increase;   // 함수 리턴
}

var counter1 = makeCounterFunction(0);   // 변수에 Increase 함수 저장 후 호출
var counter2 = makeCounterFunction(10);   // 변수에 Increase 함수 저장 후 호출

counter1();
counter2();
// counter1 함수가 호출되었을 때의 count변수와 counter2 함수가 호출되었을 때의 count 변수가 다름 (closure 때문에 발생한 현상)
// makeCounterFunction 호출시 Increase 함수가 생성되며 count변수를 포함하는 environment가 하나의 클로저로 만들어지기 때문임
// 다음에 makeCounterFunction이 호출되었을 때, 해당 함수의 environment가 새로 만들어지고 Increase 함수가 생성되며 이때의 envrionment가 새로운 클로저로 만들어짐
// 따라서 counter1에 저장된 함수와 counter2에 저장된 함수를 호출하였을 때,  count변수가 서로 다른것임
// counter1, counter2 함수를 가지고는 counter 변수의 값을 직접 제어할 수 없음
// 왜냐하면 count변수는 makeCounterFunction함수 내에 존재하고, 우리가 가지고 있는 것은 Increase 함수뿐이다
// Increase함수는 count에 접근할 수 있으나 우리가 이 함수밖에서 count 변수에 직접 접근할 수 있는 방법은 없기 때문이다
```
