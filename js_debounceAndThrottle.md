```js
// 防抖函数
function debounce(func, wait, immediate) {
    let timeout, result;
    let decounced = function () {
        let context = this;
        let args = arguments;
        clearTimeout(timeout)
        if(immediate) {
            let callNow = !timeout;   
            timeout = setTimeout(() => {
                timeout = null;
            }, wait);
        // 立即执行
            if(callNow){
                result = func.apply(context, args)
            }
        }else{
            // 不会立即执行
            timeout = setTimeout(function () {
                result = func.apply(context, args);
            },wait);
        }
        return result;
    }
    decounced.cancel = function() {
        clearTimeout(timeout);
        timeout = null;
    }
    return decounced;
}
```

```js
function throttle(func, wait, options) {
    let context, args, timeout;
    let previous = 0;
    if (!options) options = {};
    let later = function () {
        previous = new Date().valueOf();
        timeout = null;
        func.apply(context, args);
    }
    return function () {
        context = this;
        args = arguments;
        let now = new Date().valueOf();
        if (options.leading === false && !previous ) {
            previous = now;
        }
        if (now - previous > wait) {
            // 第一次会直接执行
            if (timeout) {
                clearTimeout(timeout);
                timeout = null;
            }
            func.apply(context, args);
            previous = now;
        }else if (!timeout && options.trailing !== false) {
            // 最后一次也会被执行
            timeout = setTimeout(later, wait);
        }
    }
}
```

