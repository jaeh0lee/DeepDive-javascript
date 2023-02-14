## var 키워드의 문제점 
- 변수중복 허용 
```
var x = 1
var y = 1;

var x = 100
var y;

console.log(x) // 100
console.log(y) // 1
```

### 함수 레벨 스코프 
var 키워드로 선언한 변수는 오로지 함수의 코드 블록만을 지역 스코프로 인정한다
따라서 함수 외부에서 var 키워드로 선언한 변수는 코드블록 내에서 선언해도 모두 전역 변수가 된다.

```
var x = 1
if(true){
    var x = 10
}
console.log(x) // 10
```

- 함수레벨 스코프는 전역변수를 남발할 가능성을 높인다 이로인해 의도치 않게 전역 변수가 중복 선언되는 경우가 발생한다.

var 키워드로 변수를 선언하면 변수 호이스팅에 의해 변수 선언문이 스코프의 선두로 끌어올려진것처럼 동작한다 즉 변수 호이스팅에 의해 var 키워드로 선언한 변수는 변수 선언문 이전에 참조할수 있다 단 할당ㅁ누 이전에 변수를 참조하면 언제나 undefined를 반환한다.

### let 키워드
- let 키워드는 변수 중복 선언을 금지한다.

```
let bar = 123;
let bar = 245 // Error
```

- let 키워드를 사용하면 모든 코드블록(함수, if, for문 , while문, try/catch 등) 지역 스코프로 인정하는 블록 레벨 스코프를 따른다.

```
let i = 10;
function foo(){
    let i = 100;
    for(let i = 1; i < 3; i++){
        console.log(i) // 0,1,2
    }
    console.log(i) // 100;
}
console.log(i) // 10;

```

## 변수호이스팅 
- let 키워드로 선언한 변수는 변수 호이스팅이 발생하지 않는다 
```
console.log(foo) // Error
let foo 
```
> let 키워드로 선언한 변수는 **"선언단계"** 와 **"초기단계"**가 분리되어 진행된다.

### 전역객체와 let 

- let은 전역객체가 될수 없다 
```
let x = 1;
console.log(window.x) // Error
console.log(x) // 1
``` 

### const 키워드
- const 키워드도 let 키워드와 마찬가지로 블록레벨 스코프를 가지며 변수 호이스팅이 발생하지 않는다.
- 상수도 값을 저장하기 위한 메모리 공간이 필요하므로 변수라고 할수 있다.

### const 키워드와 객체

- const 키워드로 선언된 변수에 객체를 할당한 경우 값을 변경할수 있다
```
const person = {
    name : "Lee"
}

person.name = "Kim"
console.log(person) // {name : "Kim"}
```

- const 키워드는 재할당을 금지할뿐 '불변'을 의미하지는 않는다.

**변수 선언에는 기본적으로 const 를 사용하고 let 은 재할당이 필요한 경우에 한정해 사용하는것이 좋다 .**