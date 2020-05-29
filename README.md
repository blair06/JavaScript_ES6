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

**"var 키워드로 선언된 변수는 선언 단계와 초기화 단계가 한번에 이루어진다."**
즉, 스코프에 변수를 등록(선언 단계)하고 메모리에 변수를 위한 공간을 확보한 후, undefined로 초기화(초기화 단계)한다. 따라서 스코프에 변수가 존재하기 때문에 변수 선언문 이전에 변수에 접근하여도 에러가 발생하지 않고 undefined를 반환한다. 이러한 현상을  호이스팅이라 한다.

**"let 키워드로 선언된 변수는 선언 단계와 초기화 단계가 분리되어 진행된다."**
즉, 스코프에 변수를 등록(선언단계)하지만 초기화 단계는 변수 선언문에 도달했을 때 이루어진다. 이 때문에 초기화 이전에 변수에 접근하려고 하면 참조 에러(ReferenceError)가 발생한다.  
스코프의 시작 지점부터 초기화 시작 지점까지의 구간을  "일시적 사각지대(Temporal Dead Zone; TDZ)"라고 한다.

----------

## **템플릿 리터럴 (Template literal)**

ES6는 템플릿 리터럴(Template literal)이라고 불리는 새로운 문자열 표기법을 도입하였다.일반적으로 문자작성시 ''(작은 따옴표) 혹은 ""(큰 따옴표)를 사용하였으나 ES6에선 `` (백틱 문자)를 사용한다.

### ****템플릿 리터럴 (Template literal)****

-   문자열내의 공백을 있는 그대로 제공한다
-   작은 따옴표와 큰따옴표를 혼용할 수 있다
-   문자열 인터폴레이션을 제공한다

```
const tip = `템플릿 리터럴은 '작은 따옴표'과 "큰 따옴표"를 혼용할 수 있다.`;
```

### ****문자열 인터폴레이션(String Interpolation)****

템플릿 리터럴은 + 연산자를 사용하지 않아도 간단한 방법으로 새로운 문자열을 삽입할 수 있는 기능을 제공한다  

-   ${표현식}

```
const name = 'hyewon';

// ES5
console.log('My name is ' + name + '.');

// ES6
console.log(`My name is ${name}.`);

//인터폴레이션 내의 표현식은 문자열로 강제 타입 변환된다.
//2+3 = 5
console.log(`2 + 3 = ${2+3}`);
```

  

### ****ES6 코드 사용 사례 & 효과****

일반적인 문자열에서 줄바꿈은 허용되지 않고, 공백(white-space)를 표현하기 위해서는 이스케이프시퀀스를 사용하여야 한다. 하지만 ES6 템플릿 리터럴은 일반적인 문자열과 달리 여러 줄에 걸쳐 문자열을 작성할 수 있으며 템플릿 리터럴 내의 모든 공백들은 있는 그대로 적용된다.

```
const example = "<table border='1'>\n<tr>\n<td>테이블</td>\n</tr>\n</table>";
```

하지만 ES6 템플릿 리터럴은 일반적인 문자열과 달리 여러 줄에 걸쳐 문자열을 작성할 수 있으며 템플릿 리터럴 내의 모든 공백들은 있는 그대로 적용된다.

```
const example = `<table>
	<tr>
    <td>테이블</td>
    </tr>
</table>`;
```
-------------
## **화살표 함수(arrow function)**

ES6의 화살표 함수(Arrow function)는 function 키워드 대신 화살표(=>)를 사용하여 보다 간략하게 함수를 선언할 수 있다

### **화살표함수 작성 방법**

매개변수 지정

-   매개변수가 없을 경우

```
() => { ... }
```

-   매개변수가 한개인경우
-   소괄호를 생략할 수 있다.

```
x => { ... }
```

-   매개변수가 여러 개인 경우
-   소괄호를 생략할 수 없다.

```
(x, y) => { ... }
```

함수 몸체 지정

-   single line인 경우
-   함수가 한줄이라면 중괄호 생략가능
-   암묵적으로 return

```
x => { return 2 + x }
x => 2 + x 
```

-   multi line인 경우

```
() => {          
  const x = 5;
  return 2 + x;
};
```

### ****ES6 코드 사용 사례 & 효과****

일반적인 함수 표현식보다 표현이 간결하다.

```
// ES5
var arr = [1, 2, 3];
var pow = arr.map(function (x) {
  return x * x;
});

console.log(pow); // [ 1, 4, 9 ]
```

```
// ES6
const arr = [1, 2, 3];
const pow = arr.map(x => x * x);

console.log(pow); // [ 1, 4, 9 ]
```

자바스크립트의 경우 함수 호출 방식에 의해 this에 바인딩할 어떤 객체가 동적으로 결정된다.  
콜백 함수 내부의 this는 전역 객체 window를 가리킨다.  
[JavaScript VS Java : This란?](https://hae-ong.tistory.com/14)

[](https://hae-ong.tistory.com/14)

[JavaScript vs Java] This

나는 Java를 먼저 배워서 JS에서의 this또한 당연히 Java와 같겠거니 생각했었다. 때문에 이부분의 개념은 넘어가도 되겠거니 했으나...크나큰 착각이었다. Java에서의 this Java에서의 this는 객체 자신(

hae-ong.tistory.com

화살표 함수는 함수를 선언할 때 this에 바인딩할 객체가 정적으로 결정된다. 일반 함수와는 달리 화살표 함수의 this는 언제나 상위 스코프의 this를 가리킨다 (Lexical this - Lexical Scope와 유사하다. Lexical Scope는 차후 정리 예정)  
call, apply, bind 혹은 변수대입 없이 상위 스코프에 this를 고정시킬 수 있다.  
(단,  call, apply, bind 메소드를 사용하여 다른 객체로 변경이 불가하다.)

```
function Prefixer(prefix) {
  this.prefix = prefix;
}

Prefixer.prototype.prefixArray = function (arr) {
  // this는 상위 스코프인 prefixArray 메소드 내의 this를 가리킨다.
  return arr.map(x => `${this.prefix}  ${x}`);
};

const pre = new Prefixer('Hi');
console.log(pre.prefixArray(['Lee', 'Kim']));
```

### ****화살표함수의 사용을 피해야 하는 경우****

메소드를 정의할 때

메소드로 정의한 화살표 함수 내부의 this는 메소드를 호출한 객체(소유한 객체)를 가리키지 않고 상위 객체인 전역객체 window(global)를 가리킨다.

```
const introduce = {
  name: 'hyewon',
  hello: () => console.log(`Hi, My name is ${this.name}`)
};

introduce.hello(); // Hi, My name is undefined
```

생성자 함수를 사용할 때

화살표 함수는 생성자 함수로 사용할 수 없다.  
.생성자 함수는 prototype 프로퍼티가 가리키는  prototype  객체의 constructor를 사용한다. 하지만 화살표 함수는 prototype 프로퍼티를 가지고 있지 않다.

```
const Example = () => {};

//prototype프로퍼티를 가지고 있는지 검사
console.log(Example.hasOwnProperty('prototype')); // false

const example = new Example(); // TypeError: Example is not a constructor
```

addEvantListener함수의 콜백함수로 사용할 때

addEventListener 함수의 콜백 함수를 화살표 함수로 정의하면 this가 상위 컨택스트인 전역 객체 window를 가리킨다.  
function키워드로 정의된 addEventListener 함수의 콜백 함수 내부의 this는 이벤트 리스너에 타겟된 요소를 가리킨다.  

```
var btn = document.getElementById('btn');

btn.addEventListener('click', () => {
  console.log(this === window); // => true
  this.innerHTML = 'Clicked btn';
});
```

```
var btn = document.getElementById('btn');

btn.addEventListener('click', function() {
  console.log(this === btn); // => true
  this.innerHTML = 'Clicked btn';
});
```
--------------

Java, C++과 같은 클래스기반 언어들은 객체 생성 이전에 클래스를 정의하고 이를 통해 객체(인스턴스)를 생성한다. 이와달리 자바스크립트는 프로토타입 기반 객체지향 프로그래밍 언어이다. 따라서 프로토타입을 잘 이해하는 것이 중요하다. (ES6 에서 Class문법이 추가 되었지만 우리가 흔히아는 class가 아닌 prototype을 기반으로 만들어졌다)

### **객체생성원리**  

객체는 생성자를 통해 생성된다. 생성자는 새로 생성된 객체를 초기화 하는 역할을 한다.  
정해진틀을(생성자 함수) 기계에 넣어(new 연산자) 여러개 찍어낸다고 이해하면 편리하다.

function Example() {}; //생성자 함수
var obj1 = new Example(); //생성자 함수를 이용해 생성한 객체1
var obj2 = new Example(); //생성자 함수를 이용해 생성한 객체2
//obj1와 obj2는 Example이라는 같은 구조를 가지고 있다

JS에서는 생성자 선언없이도 객체 생성이 가능하다.(리터럴 방식) 하지만 이경우에도 결과적으로는 생성자를 통해 객체를 생성하는 것과 다름없다

var obj1 = {}; //빈 객체 생성
var obj1 = new Object(); // JS엔진이 1번코드를 해석하는 방식

### **Prototype Chain (프로토타입 체인)﻿**  

다음 코드를 보면 Down생성자함수는 어떤 프로퍼티도 정의되어 있지 않은 빈 함수이지만 Down함수를 통해 생성된 객체obj의 name프로퍼티를 출력해보니 this is up이라는 문구가 출력되었다. Down이 빈함수이니 obj도 빈 객체여야 하는것 아닌가? name은 대체 어디서 나타났을까?

프로토타입 체인은 객체의 프로퍼티(현 코드에선 name)를 사용할때 해당 property가 없다면, prototype 프로퍼티를 이용해 생성자 함수의 Prototype object에서 프로퍼티(현 코드에선 name)를 찾는다. 만약 Prototype object에도 해당  프로퍼티가 없다면 다시 이 과정을 반복해 상위 Prototype object에서 프로퍼티를 찾는다. 이렇게 계속 반복이 이루어지며 해당 프로퍼티를 찾게 된다면 값을 반환하고 찾지 못한다면 undefined를 반환한다.

function Up() {}
Up.prototype.name = "this is up";

function Middle() {}
Middle.prototype = new Up();

function Down() {}
Down.prototype = new Middle();

var obj1 = new Down();
console.log(obj1.name); // this is up

obj1내에 name프로퍼티가 없으니(Down 함수내에 정의된 name이 없기때문) Down함수를 생성한 Middle함수로 올라가 name을 찾아본다. 역시나 name프로퍼티가 없으므로 Middle함수를 생성한 Up 함수에서 프로퍼티를 찾아서 name을 출력한다.

이런일이 어떻게 가능할까?  

함수를 정의하면 함수가 생성되며  Prototype object가 같이 생성 된다. Prototype object에는 함수의 원형(메소드 등등)이 저장되어 있으며 생성된 Prototype object는 함수의  prototype  속성을 통해 접근할 수 있다.

![](https://k.kakaocdn.net/dn/bAfqt6/btqEwQ5stoj/Qfi2eokVv8x0djPDBhN14K/img.png)

출처: 생활코딩

__poroto__ vs prototype의 차이

__poroto__

-   __proto__  속성은 모든 객체가 가지고 있는 속성이다.
-   객체가 생성될 때 자신의 부모 객체인 프로토타입을 가리킨다.

prototype

-   함수 객체만이 가지는 프로토타입
-   함수 객체가 생성자로 사용될 때 인스턴스의 부모 역할을 하는 객체를 가리킨다.

##
