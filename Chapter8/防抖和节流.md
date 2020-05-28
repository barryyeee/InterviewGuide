# 防抖和节流

```JavaScript
//防抖函数：抖动停止后的时间超过设定的时间时执行一次函数
function debounce(func, delay) {
    var timeout;
    //返回的函数在一个抖动结束后的delay毫秒内执行func函数
    return function() {
        var context = this, args = arguments; //保存函数调用时的上下文和参数
        clearTimeout(timeout); //触发func前清除定时器
        timeout = setTimeout(function() {
            func.apply(context, args);
        }, delay); //用户停止某个连续动作delay毫秒后执行func
    };
}

//节流函数：按照设定的时间固定执行一次函数
function throttle(func, delay, mustRun) {
    var timeout;
    var starttime = new Date(); //起始的时间
    return function() {
        var context = this, args = arguments;
        var curtime = new Date(); //当前时间
        clearTimeout(timeout);
        //如果达到规定的触发时间间隔，触发func
        if(curtime - starttime >= mustRun) {
            func.apply(context, args);
            starttime = curtime;
        }
        //没有达到触发时间，重新设定计时器
        else {
            timeout = setTimeout(func, delay);
        }
    }
}

function realFunc () {
    console.log('bibibi');
}

window.addEventListener("resize", debounce(realFunc, 500));
window.addEventListener("scroll", throttle(realFunc, 1000));
```

