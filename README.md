# JS深拷贝和浅拷贝

> JS数据类型基本分为值类型和引用类型两种。而引用类型在复制的时候，复制的是栈内存中的地址，所以就出现了深拷贝和浅拷贝。

## 引用类型深拷贝：

- Array
- Object

- 数组的浅拷贝
```js
    var arrA = [1,2,3,4,5,6,7];
    var arrB = arrA; //复制的是栈内存中的地址
    arrB[2] = 20000;

    console.log(arrA); // [1, 2, 20000, 4, 5, 6, 7]
```

- 数组的深拷贝 方法1
```js
  var arrA = [1,2,3,4,5,6,7];

  var arrC = [];
  for(var i=0,len = arrA.length; i<len; i++){
    arrC[i] = arrA[i];
  }
  console.log(arrC);

  arrC[2] = 30000;
  console.log(arrA); //  [1, 2, 3, 4, 5, 6, 7]
  console.log(arrC); //  [1, 2, 30000, 4, 5, 6, 7]
```

- 数组的深拷贝 方法2
```js
  var arrA = [1,2,3,4,5,6,7];

  var arrD;
      arrD = arrA.join('').split('');

  console.log(arrD); // ["1", "2", "3", "4", "5", "6", "7"]

  // 针对此类型 number
  arrD = arrD.map(function(item){
    return Number(item);
  });
  console.log(arrD); //[1, 2, 3, 4, 5, 6, 7];

  arrD[2] = 40000;
  console.log('arrA:',arrA); // [1, 2, 3, 4, 5, 6, 7]
  console.log('arrD:',arrD); // [1, 2, 40000, 4, 5, 6, 7]
```

- 对象类型浅拷贝
```js
  var obj = {
    name: 'xiaoming',
    age: 18,
    job: 'Program Developer'
  }

  var obj1 = obj;
  obj1.age = 22;

  console.log(obj); // age: 22
  console.log(obj1); // age: 22
```

- 对象类型深拷贝 方法1
```js
  var obj = {
    name: 'xiaoming',
    age: 18,
    job: 'Program Developer'
  }

  var obj2 = {};
  for(var item in obj){
    obj2[item] = obj[item];
  }
  console.log(obj2); // {name: "xiaoming", age: 18, job: "Program Developer"}

  obj2.age = 24;
  console.log(obj); // {name: "xiaoming", age: 18, job: "Program Developer"}
  console.log(obj2); // {name: "xiaoming", age: 24, job: "Program Developer"}
```

- 对象类型深拷贝 方法2
```js
  var obj = {
    name: 'xiaoming',
    age: 18,
    job: 'Program Developer'
  }

  var obj = {
    name: 'xiaoming',
    age: 18,
    job: 'Program Developer'
  }

  var obj3;
  obj3 = JSON.parse(JSON.stringify(obj));

  console.log(obj3); // {name: "xiaoming", age: 18, job: "Program Developer"}

  obj3.age = 26;
  console.log(obj); //{name: "xiaoming", age: 18, job: "Program Developer"}
  console.log(obj3); //{name: "xiaoming", age: 26, job: "Program Developer"}

```
