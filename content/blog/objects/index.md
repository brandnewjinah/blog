---
title: Objects in Javascript
date: "2020-04-24T22:12:03.284Z"
description: "Javascript Objects"
---

현실에서 우리는 수많은 오브젝트로 둘려싸여있다. 이 글을 쓰고 있는 컴퓨터, 입고있는 옷, 가방, 신발, 집, 가구... 이 모든것이 오브젝트이다. 오브젝트는 각각 자기만의 특징이 있다. 예를 들어 내가 지금 신고있는 운동화 브랜드는 나이키이고 모델명은 P-6000, 색은 빨간색, 사이즈는 US8 이다. 자바스크립트에서 오브젝트는 이런 현실의 사물을 프로그래밍에 반영한 것이다. 

### Syntax

``` javascript
let objectName = {     
  key: 'value',      // 속성이름: 속성값. 이 합을 property 라고 부른다
};
```

``` javascript
// 나이키 운동화를 예로 들면

let nikeShoes = {     
  'model name': 'P-6000',    //띄어쓰기가 있는 속성이름은 '' 안에 넣어준다
  color: 'red',              //속성값 뒤에는 comma 를 써준다
  size: 'US8',
};
```

### 속성에 접근하는 법 accessing properties

``` javascript
// 마침표 사용하기

alert(nikeShoes.color);  //red
```

``` javascript
// [ ] 사용하기

alert(nikeShoes['model name']);  //띄어쓰기가 있는 속성이름은 [] 를 사용해서 접근한다
```

- 마침표를 쓰는게 더 편하긴 하지만 [ ]을 사용하면 any property names and variables 를 접근할 수 있다.


### add or delete

``` javascript
// 속성 더해주기

nikeShoes.price = '$50';
nikeShoes['on sale'] = true;
```

``` javascript
// 속성 빼주기

delete nikeShoes.size;
```

### 속성이 존재하는지 확인하기
``` javascript
alert("size" in nikeShoes);   //true or false
```

### Walk over all <mark>keys</mark> of an object
``` javascript
for (let key in object) {
  // executes the body for each key among object properties
}
```

``` javascript
for (let key in nikeShoes) {
  alert(key); //model name, color, size, on sale
}
```
- key 가 숫자로 시작하면 숫자 순서대로, 그렇지 않으면 저장된 순서대로 부른다.


### Using existing variables as values for property names

``` javascript
function otherShoes(color, size) {
  return {
    color: color,
    size: size,
  };
}

let shoes = otherShoes("white", 8);
alert(shoes.color);  //white
```

The use-case fo making a property froma varialbe is so common, there's a special property value shorthand to make it shorter.
``` javascript
function otherShoes(color, size) {
  return {
    color,
    size,
  };
}
```

### Copying be reference
- A variable stores not the object itself, but its "address in memory", in other words, "a reference" to it.
- Object is stored somewhere in memory. And the variable has a "reference" to it.
- When an object variable is copied - the reference is copied, the object is not duplicated.





