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
 
    EXAMPLES
    size([1, 2, 3, 4, 5]); // 5
    size('size'); // 4
    size({ one: 1, two: 2, three: 3 }); // 3
```
