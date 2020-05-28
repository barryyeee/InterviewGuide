# 闭包实现单例模式

```javascript
var SingleTon = function(){
    var instance;
    class CreateSingleTon {
        constructor (name) {
            if(instance) return instance;
            this.name = name;
            this.getName();
            return instance = this;
        }

        getName() {
            return this.name;
        }
    }
    return CreateSingleTon;
}();

var a = new SingleTon('instance1');
console.log(a.getName()); //输出instance1
var b = new SingleTon('instance2');
console.log(b.getName()); //输出instance1
console.log(a === b); //输出true
```

