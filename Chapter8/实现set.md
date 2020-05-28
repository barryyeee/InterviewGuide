# 实现set

```javascript
class mySet {
    constructor() {
        this.items={};//js对象不允许一个键指向两个不同的属性→保证集合里元素都是唯一的
    }
    //判断集合中是否存在val元素
    has(val) {
        return this.items.hasOwnProperty(val);
    }
    //向集合中添加元素
    add(val) {
        if(!this.has(val)) {
            this.items[val] = val;
            return true;
        }
        else {
            return false;
        }
    }
    //删除集合中的指定元素
    remove(val) {
        if(this.has(val)) {
           delete this.items[val];
        }
    }
    //清空集合中的元素
    clear() {
        this.items={};
    }
    //集合的大小
    size() {
        /*Object.keys()返回给定对象所有可枚举属性的字符串数组*/
        return Object.keys(this.items).length;
    }
    //获取集合中的所有元素
    values(){
        let res=[];
        Object.keys(this.items).forEach(item=>{
            res.push(this.items[item]);
        })
        return res;
    }
}

var set = new mySet();
set.add(3);
set.add(1);
set.add(7);
set.add(0);
console.log(set.size()); //输出4
set.remove(3);
console.log(set.values()); //输出[ 0, 1, 7 ]
console.log(set.has(5)); //输出false
set.clear();
console.log(set.size()); //输出0
```

