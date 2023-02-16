### this란 

- 생성자 함수 내부에서는 프로퍼티 또는 메서드를 추가하기 위해 자신이 생성할 인스턴스를 참조할수 있어야 한다.
- 생성자 함수로 인스턴스를 생성하려면 먼저 생성자 함수가 존재해야 한다
- 생성자 함수를 정의하는 시점에는 아직 인스턴스를 생성하기 이전이므로 생성자 함수가 생성할 인스턴스를 가리키는 식별자를 알수없다, 따라서 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 특수한 식별자가 필요하다, 이를 위해 자바스크립트는 this라는 특수한 식별자를 제공한다.

**this는 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 자기 참조 변수다 this를 통해 자신이 속한 객체 또는 자신이 생성할 인스턴스의 프로퍼티나 메서드를 참조할수 있다.**

> this 바인딩이란 : this바인딩은 this(키워드로 분류되지만 식별자 역활을 한다)와 this가 가르킬 객체를 바인딩하는것이다.

**객체 리터럴**
```
cosnt circle = {

radius : 5
getDiameter(){
    return 2 * this.radius;
  }
};
console.log(circle.getDiameter()) // 10
```

**생성자 함수**
```
function Circle(radius){

    this.radius= radius
}

Circle.prototype.getDiameter = function(){
    return 2 * this.radius
}

// 인스턴스 생성
const circle = new Circle(5)
console.log(circle.getDiameter()) // 10
```

> this는 코두 어디에서든 참조가 가능한다 전역에서도 함수 내부에서도 참조할수 있다

```
// 전역
console.log(this)

// 일반 함수에서 this도 전역객체 window를 가르킨다
function square(number){
    console.log(this);
    return number * number
}
square(2)

const person = {
    name : "LEE",
    getName(){
        // 메서드 내부에서 this는 메서드를 호출한 객체를 가리킨
        console.log(this)
        return this.name
    }
}
console.log(person.getName()) // Lee


function Person(name){
    this.name = name;

    console.log(this)
}

const me = new Person('Lee')
```

- 화살표 함수 내부의 this는 상위 스코프의 this를 가리킨다.