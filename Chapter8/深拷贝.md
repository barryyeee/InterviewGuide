# 深拷贝

```javascript
//一般对象和数组对象的克隆
function deepClone(obj) {
    /*数组是对象，但是和对象又有一定区别，所以需要判断newObj是数组还是对象*/
    var newObj = obj instanceof Array ? []:{};
    for(let i in obj) {
        let tmp = typeof obj[i] == 'object' ? deepClone(obj[i]) : obj[i];
        newObj[i] = tmp;
    }
    return newObj;
}

var arr = [1,4,5,1,0];
var _arr = deepClone(arr);
arr[3] = 7; //测试是否为深拷贝
console.log(arr); //输出[ 1, 4, 5, 7, 0 ]
console.log(_arr); //输出[ 1, 4, 5, 1, 0 ]

//原始值或包装类的克隆（String Boolean Number）
function baseClone(base) {
    return base.valueOf();
}

//Date类型：日期类定义的valueOf()方法会返回它的一个内部表示：1970年1月1日以来的毫秒数
Date.prototype.clone = function() {
    return new Date(this.valueOf());
};

//正则对象RegExp
RegExp.prototype.clone = function() {
    var pattern = this.valueOf();
    var flags = '';
    flags += pattern.global ? 'g' : '';
    flags += pattern.ignoreCase ? 'i' : '';
    flags += pattern.multiline ? 'm' : '';
    return new RegExp(pattern.source, flags);
};
```

