# JavaScript_ES6
## **let & const**

대부분의 프로그래밍 언어는 블록 레벨 스코프(Block-level scope)를 따르지만 자바스크립트는 함수 레벨 스코프(Function-level scope)를 따른다.

**함수 레벨 스코프(Function-level scope)**  
함수 내부에서 선언한 변수는 지역 변수이며 함수 외부에서 선언한 변수는 모두 전역 변수이다.  
**블록 레벨 스코프(Block-level scope)**
모든 코드 블록(함수, if 문, for 문, while 문, try/catch 문 등) 내에서 선언된 변수는 코드 블록 내에서만 유효하며 코드 블록 외부에서는 참조할 수 없다. 즉, 코드 블록 내부에서 선언한 변수는 지역 변수이다.

**let과 const 키워드 도입배경**  
사용이 편리하다는 장점이 있지만 전역 변수는 유효 범위(scope)가 넓어서 어디에서 어떻게 사용될 것인지 파악하기 힘들며 비순수함수에 의해 의도하지 않게 변경될 수도 있어서 복잡성을 증가시키는 원인이 된다. 따라서 변수의 스코프는 좁을수록 좋다.  

const

-   블록 범위
-   값이 지정되면 나중에 바꿀 수 없다
-   재선언 될 수 없다

```
const name = "hyewon" 
name = "blair" // Error
```

  
let

-   블록 범위
-   값이 지정되어도 값을 바꿀 수 있다
-   중복선언은 불가능하다

```
function test() {
	let x = "a" 
    if (true) {
    	let x = "b" 
        console.log(x); // b 
        } 
    console.log(x); // a 
}
```

#### **ES6 코드 사용 사례 & 효과**

기존에는 각각의 변수가 값이 변하는 것인지 변하지 않는 것인지를 구분하기 어려웠다

```
var user = ?
var age = ? 
var number = ?
```

새롭게 바꾼 코드에서는 변수(상수)만 봐도 바뀔 수 있는 값인지 아닌지 구분하기 쉬워졌다.

```
const user = ? //상수
let age = ? //변수
const number = ? //상수
```

일단 const로 상수선언을 한 후에 프로그래밍하면서 값변경이 필요한 부분들을 let으로 고쳐주면서 사용한다

----------

## **호이스팅(Hoisting)**

var 선언문이나 function 선언문 등을 해당 스코프의 선두로 옮긴 것처럼 동작하는 특성을 말한다.  
자바스크립트는 ES6에서 도입된 let, const를 포함하여 모든 선언(var, let, const, function, function *, class)을 호이스팅한다

**변수생성 3단계**  
**선언 단계(Declaration phase)**  
변수를 변수 객체(Variable Object)에 등록한다. 이 변수 객체는 스코프가 참조하는 대상이 된다.

**초기화 단계(Initialization phase)** 
변수 객체(Variable Object)에 등록된 변수를 위한 공간을 메모리에 확보한다.  
이 단계에서 변수는 undefined로 초기화된다.

**할당 단계(Assignment phase)**  
undefined로 초기화된 변수에 실제 값을 할당한다.
