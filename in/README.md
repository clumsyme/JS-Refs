# in 与 includes、has

恰如`for ... in`，JavaScript中`in`也并不表示元素是否存在于容器中。

```js
12 in [1, 12, 3]

// false
```

若指定属性在指定对象中，`in`运算符才返回`true`。

```js
2 in ['hello', 'world', 'hi']
// true

'length' in ['hello', 'world', 'hi']
// true
```

## String.prototype.includes() 与 Array.prototype.includes()

可用这两个方法判定字符串中是否包含子串，以及数组中是否包含元素。

```js
'to be or not to be'.includes('to be')
// true

[1, 2, 25, 38, 69].includes(25)
// true
```

## 其他容器类

### Map 与 Set
使用`Map.prototype.has(key)`及`Set.prototype.has(key)`确定Map对象是否含有键值。

```js
var map = new Map([['a', 1], ['b', 2]])
map.has('a')
// true

var set = new Set([1, 2, 1, 2, 3, 1, 3])
set.has(1)
// true
```

**私以为python中统一使用`in`即有统一性又符合人的逻辑*