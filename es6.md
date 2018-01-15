# 数组的复制

``` js
  let arr = [1,2,3]
  let arr1 = arr.slice(0)
  let arr1 = [...arr,4]
  arr1.push(4)
  console.log(arr,arr1)

  let name = 'lgh'
          let age = 26
          let obj = {
    name,
    age,
    say(){
      console.log(this.name);
    }
  }
  obj.say()
```

# es6 类的写法

- class内部只能写方法，并且方法之间不能加逗号
- constructor函数 当执行 new + class名 就会默认执行
- es6构造函数的写法

  ```js
  class Person{
    constructor(name){
      this.name = name
    }
    say(){
      console.log('hello')
    }
  }

  let people = new Person('zhang')
  console.log(people)
  people.say()
  ```

# 之前的构造函数写法

```js
  function Person(firstname){
    this.firstname = firstname
  }

  Person.prototype.say = function () {
      console.log('hello')
  }

   let people = new Person('zhang')
   console.log(people)
   people.say()
```

# 之前的继承

```js
   function Son(name){
     this.name = name
   }
   Son.prototype = people
   var son = new Son('zzt')
   console.log(son.name)
   son.say()
```

# es6的继承写法

- super 是处理this指向的 如果继承的话，子 类constructor内部必须添加super()
- 向super内部传参相当于向继承的父类传参
- constructor传入参数，用super接受，通过这个方式向父类传参

  ```js
  class Son extends Person{
      constructor(name,firstname){
      super(firstname)
      this.name = name
    }
    jump(){
      console.log('jump')
    }
  }

  var son = new Son('hahaha','张')
  son.say()
  son.jump()
  console.log(son.name,son.firstname)
  ```

  # 数组的方法

- 之前数组的一些方法

  ```js
  1.filter //过滤 let objArr = [ {name:'liu',age:10}, {name:'zhang',age:11}, {name:'wang',age:15} ]

  let newArr = objArr.filter(function(item){ return item.age < 15<br>
  }) let newArr = objArr.filter(item => item.age < 15 && item.name === 'zhang') console.log(newArr)

  2.findIndex 查找满足条件的索引 let arr = [1,2,3,4,5] let num = arr.findIndex(item => item === 3) console.log(num);//2

  3.map 映射 let newArr = arr.map(item => item * item) console.log(newArr)//[1,4,9,16,25]

  4.find 查找符合条件的元素 let arr1 = [ {name:'zhang',age:14}, {name:'liu',age:14}, {name:'zhang',age:16} ] let obj = arr1.find(item => item.name === 'zhang') console.log(obj);

  5.sort 排序 arr.sort((a,b) => a - b)

  6.reduce 累加（mdn）

  7.Object.keys() 拿到一个包括obj对象的所有属性值的数组 let obj = { name:'sunny', age:20, say(){ console.log(this.name) } }

  // for(let i in obj){ // console.log(i) // console.log(obj[i]) // } let arr = Object.keys(obj) console.log(arr)

  8.Object.assign(obj,obj1)
    let obj = {
      name:'zzt',
      age:10
    }
    //let obj1 = {...obj}
    //Object.assign(obj1,obj2,...)
    //将第一个参数之后的对象合并到第一个对象参数内
    let obj1 = Object.assign({},obj,{tall:100})
    obj1.name = 'zzt'
    console.log(obj1,obj)
  ```
***
## es6
1. let/const   es6 声明变量的方式
- (1)拥有块级作用域  只要在大括号内声明就会形成作用域
- (2)同一个作用域下不允许重复声明相同的变量
- (3)变量声明不提升    ？
```js
{
  let a
  console.log(a)
}  //封装a这个变量
```
- (4) const 用来定义常量，不允许被修改
2. 解构赋值
```js
// {
//   let a = 10
//   console.log(a)
// }
（1）var username = 'lgh'
    var age = 26
    var obj = {
        username,
        age
    }//对象的解构赋值  对象的属性和值的名字相同时
    console.log(obj);

（2）var [a,b,c] = [1,2,3]

    console.log(a,b,c);//数组的解构赋值  一一对应



（3）function fun(username) {//{name} = obj  相当于name = obj.name   对象的解构赋值
      console.log(username);
    }
    var obj1 = {
      name:'lgh',
      age:26
    }
    fun(obj1)

    var {name} = obj1
    fun(name)
```

3. 字符串模板
```js
  let username = 'lgh'
  let age = 18
  let c = `my name is ${username},my age is ${age}`
  console.log(c) //字符串模板
```

4. 箭头函数
```js
  let [a,b] = [1,2]
  // function add(a,b) {
  //   console.log(a+b);
  // }
  // 箭头左边是参数，大于一个参数时必须使用小括号
  // 当只有一个参数的时候，小括号可以省略
  // 箭头右边是要做的事，当要做的事不止一句的时候，必须使用大括号
  // 当只有一句执行时候可以省略大括号，但是同时这句会被当做该函数的返回值
  let add = (a,b) => console.log(a+b) //箭头函数
  add(a,b)
```

- (1)函数体内的this对象，就是定义时所在的对象，而不是使用时所在的对象。
- (2)不可以当做构造函数,也就是说，不可以使用new命令，否则会抛出一个错误
- (3)不可以使用arguments对象，该对象在函数内不存在。如果要用，可以用rest参数替代。
5. 函数参数
- 参数的默认值
- 函数声明的时候在小括号内部直接给参数赋值相当于给了参数默认值。
```js
  function fun(x=0,y=0){
    return x*y
  }
  var z = fun()
  console.log(z)
```

- 函数参数的集合
- rest 剩余参数
```js
  let sum = (a,...rest) => console.log(rest)
  sum(1,2,3,4,5,6,7)  //输出的是一个数组，与arguments（是一个类数组）不同。
```

6. 扩展操作符（...）
- 数组的扩展
```js
  var arr = [1,2,3]
  var arr1 = [4,5,6]
  var arr2 = [7,8,9]
  var newArr = arr.concat(arr1,arr2)
  var newArr = [...arr,...arr1,...arr2]
输出：[1,2,3,4,5,6,7,8,9]
```
- 对象的扩展
```js
  var obj = {
    name = 'zzt'
    age = 10
  }
  var obj1 = {
    say:()=>console.log(this.name)
  }
  var newObj = {...obj,...obj1}
输出：{name:'zzt',age:10,say:()=>console.log(this.name)}
```
# es6模块导出 导入

- 命名导出 导入

  ```js
  let a = 10,b=20
  export {a}//导出
  import {a as b} from './demo' //导入

  export {a,b}
  import * as obj from './deml' //全部导入
  ```

- 默认导出

```js
  // 默认导出只能有一个，不使用大括号
  // let a = () => console.log('11')
  let a = 110
  let b = 220
  let c = 330
  export default a
  export {b,c}

// 默认导入
  // require('./demo.js')
  // import b from './demo.js'
  import * as obj from './demo'
  console.log(obj)
```

# lodash js扩展库

```js
  let _ = require('lodash')
  console.log( _ )
  按需加载
  import array from 'lodash/array'
  let arr = [1,2,3,4,5,6,7,8,9,3]
  let num = array.findIndex(arr,item => item ===3,3)
  console.log(num)
```
