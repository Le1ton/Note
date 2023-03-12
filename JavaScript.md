# JavaScript

[article](https://github.com/stephentian/33-js-concepts#1-%E8%B0%83%E7%94%A8%E5%A0%86%E6%A0%88)

### 1. 调用栈

​	调用栈是一种数据结构，它记录了我们在程序中的位置。如果我们运行到一个函数，它就会将其放置在栈顶。当从这个函数返回的时候，就会将这个函数从栈顶弹出，这就是调用栈做的事情。

```javascript
let a = 'Hello World!';

function first() {
  console.log('Inside first function');
  second();
  console.log('Again inside first function');
}

function second() {
  console.log('Inside second function');
}

first();
console.log('Inside Global Execution Context');

// result
Inside first function
Inside second function
Again inside first function
Inside Global Execution Context
```

![img](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2018/9/20/165f539572076fe3~tplv-t2oaga2asx-zoom-in-crop-mark:4536:0:0:0.awebp)

###  2. 值类型和引用类型

JavaScript 有 5 种基本的数据类型，分别是：布尔、null、undefined、String 和 Number

- 这些基本类型在赋值时是通过值传递的

另外三种类型: Array、Function 和 Object

- 而这三种类型是通过引用来传递的，即变量赋值时只会把地址传过去

```javascript
function changeAgeAndReference(person) {
    person.age = 25;
    person = {
        name: "John",
        age: 50
    };

    return person;
}
var personObj1 = {
    name: "Alex",
    age: 30
};
var personObj2 = changeAgeAndReference(personObj1);
console.log(personObj1); // {name: 'Alex', age: 25}
console.log(personObj2); // {name: 'John', age: 50}
```

![image-20230305164009081](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20230305164009081.png)

### this

- `say("Hello world")`看做是`say.call(window,"Hello world")`的语法糖。
- 





