## map

Map数据结构类似于对象，是健值对的集合，传统的键只能是字符串，Map的挺不限于字符串，各种类型的值都可以当作键

## Set

### Set 实例的操作方法

```js
let set = new Set();
set.add(1);
set.add("1");
console.log(set.size); // 2
```

可以使用数组来初始化一个 Set ，并且 Set 构造器会确保不重复地使用这些值:

```js
let set = new Set([1, 2, 3, 4, 5, 5, 5, 5]);
console.log(set.size); // 5
```

add(value): 添加某个值，返回Set结构本身

has(value): 返回布尔值，表示该值是否为Set的成员

delete(value): 删除某个值，返回一个布尔值，表示是否成功

clear(value):清除所有成员，没有返回值

### Set遍历操作

keys():返回键名的遍历器

values(): 返回健值的遍历器

entries():返回键值对的遍历器

forEach(): 每个成员

```js
let set = new Set(['red', 'green', 'blue']);

for (let item of set.keys()) {
console.log(item);
}
// red
// green
// blue

for (let item of set.values()) {
console.log(item);
}
// red
// green
// blue

for (let item of set.entries()) {
console.log(item);
}
// ["red", "red"]
// ["green", "green"]
// ["blue", "blue"]

let set = new Set([1, 2]);
set.forEach(function(value, key, ownerSet) {
    console.log(key + "： " + value);
});
// 输出
// 1 ：1
// 2： 2
```

### ES6数组去重

```js
let arr = [1, 2, 2, 3];
let set = new Set(arr);
let newArr = Array.from(set);
console.log(newArr); // [1, 2, 3]
```

#### Set集合转化Array数组

```js
let set = new Set([1, 2, 3, 3, 4]);
let arr = Array.from(set)  //输出[1,2,3,4]
```