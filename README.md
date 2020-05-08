# utils-function
在学习[30 seconds of code](https://github.com/30-seconds/30-seconds-of-code)后记录一下，并进行分类

目录：
*  第一部分：对象


## 1. 第一部分：对象
### 1. `size`：获取数组、对象、字符串的长度.
```
const size = val =>
  Array.isArray(val)
    ? val.length
    : val && typeof val === 'object'
    ? val.size || val.length || Object.keys(val).length
    : typeof val === 'string'
    ? new Blob([val]).size
    : 0;
 
示例：
size([1, 2, 3, 4, 5]); // 5
size('size'); // 4
size({ one: 1, two: 2, three: 3 }); // 3
```
### 2. `dig`：根据给定的键，返回对象中的目标值.
```
const dig = (obj, target) =>
  target in obj
    ? obj[target]
    : Object.values(obj).reduce((acc, val) => {
        if (acc !== undefined) return acc;
        if (typeof val === 'object') return dig(val, target);
      }, undefined);
      
示例：
const data = {
  level1: {
    level2: {
      level3: 'some data'
    }
  }
};
dig(data, 'level3'); // 'some data'
dig(data, 'level4'); // undefined
```
### 3. `objectToQueryString`：返回从给定对象的键值对生成的查询字符串.
```
const objectToQueryString = queryParameters => {
  return queryParameters
    ? Object.entries(queryParameters).reduce((queryString, [key, val], index) => {
      const symbol = queryString.length === 0 ? '?' : '&';
      queryString += typeof val === 'string' ? `${symbol}${key}=${val}` : '';
      return queryString;
    }, '')
    : '';
};

示例
objectToQueryString({ page: '1', size: '2kg', key: undefined }); // '?page=1&size=2kg'
```
### 4. `matches`：比较两个对象以确定第一个对象是否包含第二个对象.
```
const matches = (obj, source) =>
  Object.keys(source).every(key => obj.hasOwnProperty(key) && obj[key] === source[key]);


示例
matches({ age: 25, hair: 'long', beard: true }, { hair: 'long', beard: true }); // true
matches({ hair: 'long', beard: true }, { age: 25, hair: 'long', beard: true }); // false
```
### 5. `shallowClone`：创建对象的浅拷贝.
```
const shallowClone = obj => Object.assign({}, obj);

示例
const a = { x: true, y: 1 };
const b = shallowClone(a); // a !== b

```
### 6. `forOwnRight`：反向遍历对象，每个对象运行一个回调.

```
const forOwnRight = (obj, fn) =>
  Object.keys(obj)
  .reverse()
  .forEach(key => fn(obj[key], key, obj))
}

示例：
forOwnRight({ a: '1', b: 2, c: 'c' }, v => console.log(v)); // 'c', 2 ,'1'
```
### 7. `truthCheckCollection`：检查数组对象是否都存在该属性.

```
const truthCheckCollection = (collection, pre) => collection.every(obj => obj[pre])

示例：
truthCheckCollection([{ user: 'Tinky-Winky', sex: 'male' }, { user: 'Dipsy', sex: 'male' }], 'sex'); // true
```
### 8. `objectToPairs`：对象转化为键值对二维数组.

```
const objectToPairs = obj => Object.entries(obj);

示例：
objectToPairs({ a: 1, b: 2 }); // [ ['a', 1], ['b', 2] ]
```
### 9. 
