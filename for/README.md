# for ... in 与 for ... of

不同于python中的`for ...in`，JavaScript中`for ...in`迭代一个对象的属性名，
而`for ... of`则类似python，迭代一个对象的属性值。

## for ... in

`for ... in`以**任意顺序**迭代一个对象的可枚举属性。

```javascript
var dog = {
    name: 'Tom',
    age: 3,
    bark: function() {
        return this.name
    }
}
for (let attr in dog) {
    console.log(attr)
}

// name
// age
// bark
```

`for ... in`会迭代对象及其原型的属性，除非使用hasOwnProperty()方法。

```js
function Animal() {
    this.name = 'Animal'
}

function Cat() {
    this.age = 3
}

Cat.prototype = new Animal()
var cat = new Cat()

for (let attr in cat) {
    console.log(attr)
}

// age
// name

for (let attr in cat) {
    if (cat.hasOwnProperty(attr)) {
        console.log(attr)
    }
}

// age
```

### `for ... in ` 与 Array

使用`for ... in`迭代数组，将返回数组整数索引，但并不能保证按一定顺序。
如果迭代顺序重要，最好使用`for ... of`或者`.forEach`方法。

```js
for (let i in [2, 4, 6]) {
    console.log(i)
}

// 0
// 1
// 2
```

## for ... of

`for ... of`迭代一个可迭代对象(Array、Set、Map...)的属性值。

### Array

```js
for (let i of [2, 4, 6]) {
    console.log(i)
}

// 2
// 4
// 6
```

### String

```js
for (let i of 'hello') {
    console.log(i)
}

// h
// e
// l
// l
// o
```

### Map

```js
var map = new Map([['name', 'Tom'], [age, 3]])
for (let [key, value] of map) {
    console.log(key + ' is ' + value)
}

// name is Tom
// age is 3
```

### Set

```js
var set = new Set([1,1,2,3,3])
for (let value of set) {
    console.log(value)
}

// 1
// 2
// 3
```

### Generator

```js
function* fibnacci() {
    let a = b = 1
    while (true) {
        [a, b] = [b, a+b]
        yield a
    }
}

var fib = fibnacci()
for (let n of fib) {
    if (n > 10) {
        break
    }
    console.log(n)
}

// 1
// 2
// 3
// 5
// 8
```

### DOM

```js
var buttons = document.getElementsByTagName('button')
for (let button of buttons) {
    // doSomething
}
```

## forEach

`forEach`对数组的每一个元素执行一次回调函数。

`array.forEach(callback[, thisArg])`

`callback`函数接收三个参数，依次为

`currentValue`: 当前值

`index`: 当前索引

`array`: 数组

```js
[2, 4, 6].forEach(function(value, index, array) {
    console.log('index ' + index + ' is ' + value )
})

// index 0 is 2
// index 1 is 4
// index 2 is 6
```