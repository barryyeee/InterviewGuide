# 数组去重

```javascript
Array.prototype.uniq = function() {
    if(!this.length || this.length == 0) return this;
    var res = [];
    var hasNaN = false,  temp = {};
    /* {}==={}为false */
    for(var i = 0; i < this.length; i++) {
        if(typeof this[i] === 'object') {
            //当前遍历的元素是对象
            res.push(this[i]);
        }
        else if(this[i] != this[i]) {
            //NaN === NaN为false→如果当前遍历元素是NaN
            if(!hasNaN) {
                res.push(this[i]);
                hasNaN = true;
            }
        }
        else {
            //当前遍历的元素是基本数据类型
            if(!temp[typeof this[i] + this[i]]) {
                res.push(this[i]);
                temp[typeof this[i] + this[i]] = true;
            }
        }
    }
    return res;
}

function unique(arr) {
    var res = [];
    for(let i in arr) {
        if(res.indexOf(arr[i]) == -1) {
            res.push(arr[i]);
        }
    }
    return res;
}

var arr = [1, 1, '1', '1', null, null, undefined, undefined, new String('1'), new String('1'), /a/, /a/, NaN, NaN];
/*输出[1, '1', null, undefined, [String: '1'], [String: '1'], /a/, /a/, NaN]*/
console.log(Array.from(new Set(arr)));
/*输出[1, '1', null, null, undefined, [String: '1'], [String: '1'], /a/, /a/, NaN]*/
//console.log(arr.uniq()); 
/*输出[1, "1", null, undefined, String, String, /a/, /a/, NaN, NaN]*/
//console.log(unique(arr));
```



参考：[JavaScript专题之数组去重](https://juejin.im/post/5949d85f61ff4b006c0de98b#heading-0)