# 算法片段

* 计算一个整数的阶乘

```
function factorialize(num) {
    var result = 1;
    for (var i = 1; i <= num; i++) {
        result *= i;
    }
    return result;
}
factorialize(5);
```

* 翻转字符串

```
function reverseString(str) {
    var c=str.split('').reverse().join('');
    return c;
}
reverseString("hello");
```

* 如果给定的字符串是回文，返回true，反之，返回false，如果一个字符串忽略标点符号、大小写和空格，正着读和反着读一模一样，那么这个字符串就是palindrome(回文)

```
function palindrome(str) {
    var b=str.replace(/\s/ig,'');
    var d=b.replace(/[\ |\~|\`|\!|\@|\#|\$|\%|\^|\&|\*|\(|\)|\-|\_|\+|\=|\||\\|\[|\]|\{|\}|\;|\:|\"|\'|\,|\<|\.|\>|\/|\?]/g,"");
    var c=d.toLowerCase();
    var a=c.split("").reverse().join("");
    return a==c;
}
palindrome("race car");
```

* 找到提供的句子中最长的单词，并计算它的长度

```
function findLongestWord(str) {
    var a = str.split(" ");
    var b = [];
    for (var i = 0; i < a.length; i++) {
        b.push(a[i].length);
    }
    b.sort(function(a, b) {
        return a - b;
    });
    return b[b.length - 1];
}
findLongestWord("The quick brown fox jumped over the lazy dog");
```

* 确保字符串的每个单词首字母都大写，其余部分小写

```
function titleCase(str) {
    var a = str.toLowerCase().split(" ");
    var b = [];
    for (var i in a) {
        b.push(a[i][0].toUpperCase() + a[i].substring(1));
    }
    var c = b.join(" ");
    return c;
}
titleCase("I'm a little tea pot");
```

* 大数组中包含了4个小数组，分别找到每个小数组中的最大值，然后把它们串联起来，形成一个新数组

```
function largestOfFour(arr) {
    var b = [];
    for (var i in arr) {
        b.push(arr[i].sort(function(a, b) {
            return a - b;
        }).pop());
    }
    return b;
}
largestOfFour([
    [4, 5, 1, 3],
    [13, 27, 18, 26],
    [32, 35, 37, 39],
    [1000, 1001, 857, 1]
]);
```

* 检查一个字符串(str)是否以指定的字符串(target)结尾,如果是返回true;如果不是返回false

```
function confirmEnding(str, target) {
    return str.substr(-target.length) == target;
}
confirmEnding("Bastian", "n");
```

* 重复一个指定的字符串 num次，如果num是一个负数则返回一个空字符串

```
function repeat(str, num) {
    var b = [];
    if (num <= 0) {
        return "";
    } else {
        for (var i = 1; i <= num; i++) {
            b.push(str);
        }
        return b.join('');
    }
    return str;
}
repeat("abc", 3);
```

* 截断一个字符串！如果字符串的长度比指定的参数num长，则把多余的部分用...来表示,插入到字符串尾部的三个点号也会计入字符串的长度，如果指定的参数num小于或等于3，则添加的三个点号不会计入字符串的长度

```
function truncate(str, num) {
    var b;
    if (num >= str.length) {
        return str;
    } else if (num > 3) {
        b = str.slice(0, num - 3);
        return b + "...";
    } else {
        b = str.slice(0, num);
        return b + "...";
    }
    return str;
}
truncate("A-tisket a-tasket A green and yellow basket", 11);
```

* 把一个数组arr按照指定的数组大小size分割成若干个数组块,例如:chunk([1,2,3,4],2)=[[1,2],[3,4]];chunk([1,2,3,4,5],2)=[[1,2],[3,4],[5]]

```
function chunk(arr, size) {
    var a = 0;
    var b = [];
    while (a < arr.length) {
        b.push(arr.slice(a, a += size));
    }
    return b;
}
chunk(["a", "b", "c", "d"], 2);
```

* 返回一个数组被截断n个元素后还剩余的元素

```
function slasher(arr, howMany) {
    var b = [];
    if (howMany < arr.length) {
        b = arr.splice(0, howMany);
    } else {
        arr = [];
    }
    return arr;
}
slasher([1, 2, 3], 2);
```

* 如果数组第一个字符串元素包含了第二个字符串元素的所有字符，函数返回true

```
function mutation(arr) {
    for (var i = 0; i < arr[1].length; i++) {
        if (arr[0].toLowerCase().indexOf(arr[1][i].toLowerCase()) == -1) {
            return false;
        }
    }
    return true;
}
mutation(["hello", "hey"]);
```

* 删除数组中的所有假值

```
function bouncer(arr) {
    return arr.filter(function(e) {
        return e !== false && e !== null && e !== 0 && e !== '' && e !== undefined && !(isNaN(e) && typeof(e) !== 'string');
    });
}
bouncer([false, null, 0, NaN, undefined, ""]);
```

* 实现一个摧毁(destroyer)函数，第一个参数是待摧毁的数组，其余的参数是待摧毁的值

```
function destroyer(arr) {
    var c = [];
    var d = [];
    for (var i = 0; i < arguments.length; i++) {
        c.push(arguments[i]);
    };
    function a() {
        var b = c[0];
        c.shift();
        for (var i = 0; i < b.length; i++) {
            if (c.indexOf(b[i]) == -1) {
                d.push(b[i]);
            };
        };
    };
    a();
    return d;
}
destroyer([1, 2, 3, 1, 2, 3], 2, 3);
```

* 先给数组排序，然后找到指定的值在数组的位置，最后返回位置对应的索引

```
function where(arr, num) {
    arr.push(num);
    arr.sort(function a(a, b) {
        return a - b;
    })
    var b = arr.indexOf(num);
    return b;
}
where([40, 60], 50);
```

* 一个常见的案例就是ROT13密码，字母会移位13个位置,由'A' ↔ 'N', 'B' ↔ 'O'，以此类推,写一个ROT13函数，实现输入加密字符串，输出解密字符串

```
function rot13(str) {
    var a=[];
    var ste=str.split("");
    var pattern=/[^a-zA-Z]/;
    for (var i = 0; i < ste.length; i++) {
        if(pattern.test(ste[i])){
            a.push(ste[i]);
        }else {
            if(ste[i].charCodeAt()<65+13){
                a.push(String.fromCharCode(ste[i].charCodeAt()+26-13));
            }else {
                a.push(String.fromCharCode(ste[i].charCodeAt()-13));
            }
        }
    }
    var b=a.join('');
    return b;
}
rot13("GUR DHVPX OEBJA QBT WHZCRQ BIRE GUR YNML SBK.");
```

* 返回这两个数字和它们之间所有数字的和

```
function sumAll(arr) {
    var a=Math.max.apply(null,arr);
    var b=Math.min.apply(null,arr);
    return (a+b)*(a-b+1)/2;
}
sumAll([1, 4]);
```
