# utils-function
在学习[30 seconds of code](https://github.com/30-seconds/30-seconds-of-code)后记录一下，并进行分类

## 1. 第一部分：数组
### 1. `all`：布尔全等判断
```
const all = (arr, fn = Boolean) => arr.every(fn);

all([4, 2, 3], x => x > 1); // true
all([1, 2, 3]); // true
```
