# promise相关

```javascript
/* promise的简单实现 */
class myPromise{
    constructor (process) {
        this.status = 'pending';
        this.msg = '';
        process(this.resolve.bind(this), this.reject.bind(this));
        return this;
    }
    resolve (val) {
        this.status = 'resolved';
        this.msg = val;
    }
    reject (err) {
        this.status = 'rejected';
        this.msg = err;
    }
    then (resolve, reject) {
        if(this.status == 'resolved')
            resolve(this.msg);
        if(this.status == 'rejected')
            reject(this.msg);
    }
}

//Test
var my_promise = new myPromise(function(resolve, reject) {
    resolve('OK');
});
my_promise.then(function(val) {
    console.log(`success: ${val}`);
}, function(err){
    console.log(`failed: ${err}`);
}); //输出success: OK
```

```javascript
/*实现promiseAll的功能*/
function promiseAll(promises) {
    return new Promise(function(resolve, reject) {
        var resolvedCount = 0; //成功执行的promise个数
        var promiseNum = promises.length; //数组中一共有几个promise
        var resolvedValues = new Array(promiseNum); //保存成功解决的promise的val
        for(let i = 0; i < promiseNum; i++) {
            Promise.resolve(promises[i].then(function(val) {
                resolvedCount++;
                resolvedValues[i] = val;
                //当所有函数都正确执行了，resolve输出所有返回的结果
                if(resolvedCount == promiseNum) {
                    return resolve(resolvedValues);
                }
            }, function(err) {
                return reject(err);
            })
            )
        }
    })
}

var p1 = Promise.resolve(1);
var p2 = Promise.resolve(2);
//var p2 = Promise.reject('wrong');
var p3 = Promise.resolve(3);
promiseAll([p1, p2, p3]).then(function (results) {
  console.log(results);  
}).catch(function(err){
  console.log(err);
}); //输出[ 1, 2, 3 ]
```

