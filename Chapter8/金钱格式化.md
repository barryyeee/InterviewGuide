# 金钱格式化

```javascript
/*
 *Array.prototype.reverse() Array→String
 *Array.prototype.join() Array→String
 *String.prototype.split() String→Array
 *String.prototype.match() String→Array
*/

function transferToMoney(money) {
    if(money && money != null) {
        money = String(money);
        var left = money.split('.')[0], right = money.split('.')[1];
        right = right ? (right.length >= 2 ? '.' + right.substr(0, 2) : '.' + right + '0') : '.00';
        var tmp = left.split('').reverse().join('').match(/\d{1,3}/g);
        left = tmp.join(',').split('').reverse().join('');
        return (Number(money) < 0 ? '-' : '') + left + right;
    }
    else if(money === 0) {
        return '0.00';
    }
    else {
        return '';
    }
}
```