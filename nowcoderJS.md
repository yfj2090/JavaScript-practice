2022-7-17 | Sunday | Sunny
1. 请补全JavaScript代码，要求在页面上渲染出一个直角三角形，三角形换行要求使用"br"实现。三角形如下：
```
*
**
***
```
```js
<script>
    var triangle = document.querySelector('.triangle');
    // 补全代码
    triangle.innerHTML = `
        *<br>**<br>***
    `
</script>
```
---
2. 请补全JavaScript代码，要求以字符串的形式返回文件名扩展名，文件名参数为"filename"。
```js
<script>
const _getExFilename = (filename) => {
    // 补全代码
    const index = filename.lastIndexOf('.')
    return filename.slice(0, index) && index !== -1 ? filename.slice(index) : ''
}
</script>
```
---
3. 请补全JavaScript代码，要求返回参数数字的千分位分隔符字符串。
```js
function _comma(number) {
    // 补全代码
    /*
    分析：number可能是负数，一开始先把符号拿出来，最后输出的时候添加符号。
    1、number有可能是小数，首先做用split('.')分割整数和小数，我们只对整数做千分位分隔符。
    2、将整数用split('')做数组转换，并用reverse()颠倒整数数组中元素的顺序，从左到右用silce()取3位元素为一组，并reverse()3个数字后，join('')组合成字符串，push()入新的数组，让新数组变成每个元素都是三位的字符串。
    3、将数组拼接成字符串，将新数组reverse()颠倒到正确的顺序，用join(',')加入千分位分隔符。
    4、最后对符号和小数位进行判断和组合，return出最终结果。
    **/
    const negative = number < 0 ? '-' : ''
    let [left, right] = Math.abs(number).toString().split('.')
    let arrLeft = left.split('').reverse()
    let newArr = []
    for (let i = 0; i < arrLeft.length; i += 3) {
        newArr.push(arrLeft.slice(i, i + 3).reverse().join(''))
    }
    return `${negative + newArr.reverse().join(',')}${right ? '.' + right : '' }`
}
```
---
4. 请补全JavaScript代码，要求每当id为"input"的输入框值发生改变时触发id为"span"的标签内容同步改变。
注意：
1. 必须使用DOM0级标准事件（onchange）
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
    </head>
    <body>
    	<input id="input" type="text" onchange="binging(value)"/>
        <span id="span"></span>

        <script type="text/javascript">
            // 补全代码
            function binging(value) {
                const span = document.getElementById('span')
                span.innerText = value
            }
        </script>
    </body>
</html>
```
---
5. 请补全JavaScript代码，要求返回一个长度为参数值并且每一项值都为参数值的数组。
注意：
1. 请勿直接使用for/while
```js
const _createArray = (number) => {
    // 补全代码
    // Array.from()
    // from() 方法从具有 length 属性或可迭代对象的任何对象返回 Array 对象。
    /* @object	必需。需转换为数组的对象。
     * @mapFunction	可选。对数组的每个项目调用的 map 函数。
     * @thisValue	可选。执行 mapFunction 时用作 this 的值。
     */
    return Array.from({ length: number }, () => number)
}
```
---
6. 请补全JavaScript代码，该函数接收两个参数分别为旧版本、新版本，当新版本高于旧版本时表明需要更新，返回true，否则返回false。

**注意：**
1) 版本号格式均为"X.X.X"
2) X∈[0,9]
3) 当两个版本号相同时，不需要更新
```js
const _shouldUpdate = (oldVersion, newVersion) => {
    // 补全代码
    const oldNumber = Number(oldVersion.split('.').join(''))
    const newNumber = Number(newVersion.split('.').join(''))
    return oldNumber < newNumber
}
```
---
7. 请补全JavaScript代码，实现一个函数，要求如下：

1) 根据输入的数字范围[start,end]和随机数个数"n"生成随机数
2) 生成的随机数存储到数组中，返回该数组
3) 返回的数组不能有相同元素

**注意：**
1. 不需要考虑"n"大于数字范围的情况
```js
const _getUniqueNums = (start, end, n) => {
    let arr = []
    while(arr.length < n) {
        let number = Math.round(Math.random()*end + start)
        if (arr.indexOf(number) === -1) {
            arr.push(number)
        }
    }
    return arr
}
```
---
8. 请补全JavaScript代码，根据预设代码中的数组，实现以下功能：

1) 列表只展示数组中的name属性
2) 实现点击"销量升序"按钮，列表内容按照销量升序重新渲染
3) 实现点击"销量降序"按钮，列表内容按照销量降序重新渲染
注意：
1. 必须使用DOM0级标准事件（onclick）
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <button class='up'>销量升序</button>
        <button class='down'>销量降序</button>
        <ul></ul>

        <script>
            var cups = [
                { type: 1, price: 100, color: 'black', sales: 3000, name: '牛客logo马克杯' },
                { type: 2, price: 40, color: 'blue', sales: 1000, name: '无盖星空杯' },
                { type: 4, price: 60, color: 'green', sales: 200, name: '老式茶杯' },
                { type: 3, price: 50, color: 'green', sales: 600, name: '欧式印花杯' }
            ]
            var ul = document.querySelector('ul');
            var upbtn = document.querySelector('.up');
            var downbtn = document.querySelector('.down');
            // 补全代码
            
            function sortUp(a, b) {
                return a.sales - b.sales
            }
            
            function sortDown(a, b) {
                return b.sales - a.sales
            }
            
            upbtn.onclick = function() {
                ul.innerHTML = ''
                cups.sort(sortUp).forEach(v => {
                    let li = document.createElement('li')
                    li.innerHTML = v.name
                    ul.append(li)
                })
            }
            
            downbtn.onclick = function() {
                ul.innerHTML = ''
                cups.sort(sortDown).forEach(v => {
                    let li = document.createElement('li')
                    li.innerHTML = v.name
                    ul.append(li)
                })
            }
        </script>
    </body>
</html>
```
---
9. 请补全JavaScript代码，该函数接受两个参数分别为数组、索引值，要求在不改变原数组的情况下返回删除了索引项的新数组。

**本题考点：闭包、匿名函数**
```js
const _delete = (array,index) => {
    // 补全代码
    return array.filter((v, i) => i !== index)
}
```
```js
const _delete = (array,index) => {
    // 补全代码
    let newArr = [...array]
    newArr.splice(index, 1)
    return newArr
}
```
---
10. 请补全JavaScript代码，将预设代码中的"people"数组渲染在页面中。实现下面的列表：

牛油1号 20岁
牛油2号 21岁
牛油3号 19岁
```html
<script>
    var people = [
        { name: '牛油1号', id: 1, age: 20 },
        { name: '牛油2号', id: 2, age: 21 },
        { name: '牛油3号', id: 3, age: 19 },
    ]
    var ul = document.querySelector('ul');
    ul.innerHTML = ''
    // 补全代码
    people.forEach(v => {
        let li = document.createElement('li')
        li.innerHTML = `${v.name} ${v.age}岁`
        ul.append(li)
    })
</script>
```
---
11. 请补全JavaScript代码，实现以下功能：  

1) 根据已有的person对象的注册时间求出距离当前时间的天数（天数向下取整）。
2) 将获得的天数和person数据拼接成字符串，作为h2标签的内容。
注意：使用模板字符串进行字符串拼接，字符串最终内容如：尊贵的牛客网2级用户小丽您好，您已经注册牛客网3天啦~
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <h2></h2>

        <script>
            var person = {
                level: '2',
                name: '小丽',
                registTime: '2021-11-01',
            }
            var h2 = document.querySelector('h2');
            // 补全代码
            let personTime = new Date(person.registTime).getTime()
            let nowTime = new Date().getTime()
            let days = Math.floor(nowTime - personTime)/(1000*60*60*24)
           
            h2.innerHTML = `尊贵的牛客网${person.level}级用户${person.name}您好，您已经注册牛客网${days}天啦~`
        </script>
    </body>
</html>
```
---
12. 请补全JavaScript代码，完成类的继承。要求如下：

1) "Chinese"类继承于"Human"类
2) "Human"类实现一个函数"getName"，返回该实例的"name"属性
3) "Chinese"类构造函数有两个参数，分别为"name"、"age"
4) "Chinese"类实现一个函数"getAge"，返回该实例的"age"属性

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
    </head>
    <body>
    	
        <script type="text/javascript">
            class Human {
                constructor(name) {
                    this.name = name
                    this.kingdom = 'animal'
                    this.color = ['yellow', 'white', 'brown', 'black']
                }
                // 补全代码
                getName() {
                    return this.name
                }
            }

            // 补全代码
            class Chinese extends Human {
                constructor(name, age) {
                    super(name)
                    this.age = age
                }
                
                getAge() {
                    return this.age
                }
            }
        </script>
    </body>
</html>
```
---
13. 请补全JavaScript代码，要求将字符串参数URL中的参数解析并以对象的形式返回。
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>

        <script>
            const _getParams = (url) => {
                // 补全代码
                let obj = {}
                let arr = url.split('?')[1].split('&')
                for (let i = 0; i < arr.length; i++) {
                    let temp = arr[i].split('=')
                    obj[temp[0]] = temp[1]
                }
                return obj
            }
        </script>
    </body>
</html>
```
---
14. 请补全JavaScript代码，要求根据参数动态生成"li"标签页码并插入"ul"标签下。要求如下：

1) "allItem"为总数据项个数，"pageItem"为每页的数据项个数
2) "li"标签内容为当前页码数，页码从1开始
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
    </head>
    <body>
    	<ul id="ul">
            
        </ul>
        <script type="text/javascript">
            const _createPage = (allItem, pageItem) => {
                // 补全代码
                let ul = document.getElementById('ul')
                const pageLen = Math.ceil(allItem/pageItem)
                let content = ''
                for (let i = 0; i < pageLen; i++) {
                    content += `<li>${i + 1}</li>`
                }
                ul.innerHTML = content
            }
        </script>
    </body>
</html>
```
---
15. 请补全JavaScript代码，要求将数组参数中的对象以总成绩(包括属性"chinese"、"math"、"english")从高到低进行排序并返回。
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
    </head>
    <body>
    	
        <script type="text/javascript">
        const _rank = array => {
            // 补全代码
            array.sort((a, b) => {
                const left = a.chinese + a.math + a.english
                const right = b.chinese + b.math + a.english
                return right - left
            })
            return array
        }
        </script>
    </body>
</html>
```
---
16. 请补全JavaScript代码，该函数接受两个参数分别为字符串、子字符串，要求返回子字符串在字符串中出现的频次。
```js
const _searchStrIndexOf = (str, target) => {
    // 补全代码
    let num = str.split(target).length - 1
    return num
}
```
---
17. （直角三角形）请补全JavaScript代码，实现以下功能：

1) 给"Human"构造函数的原型对象添加"getName"方法，返回当前实例"name"属性
2) 将"Chinese"构造函数继承于"Human"构造函数
3) 给"Chinese"构造函数的原型对象添加"getAge"方法，返回当前实例"age"属性
```js
function Human(name) {
    this.name = name
    this.kingdom = 'animal'
    this.color = ['yellow', 'white', 'brown', 'black']
}

function Chinese(name,age) {
    Human.call(this,name)
    this.age = age
    this.color = 'yellow'
}

// 补全代码

/* 首先通过Human.prototype.getName给“Human”的原型添加“getName”函数
* 然后通过Chinese.prototype将“Chinese”的原型挂载在“Human”构造函数的实例上
* 修复“Chinese”的原型链
* 最后通过Chinese.prototype.getAge给“Chinese”的原型添加“getAge“函数
*/
Human.prototype.getName = function() {
    return this.name
}

Chinese.prototype = new Human()
Chinese.prototype.constructor = Chinese
Chinese.prototype.getAge = function() {
    return this.age
}
```
---
18. （判断斐波那契数组）请补全JavaScript代码，要求以Boolean的形式返回参数数组是否为斐波那契数列。在数学上，斐波那契数列以如下方法定义：F(0)=0，F(1)=1, F(n)=F(n - 1)+F(n - 2)（n ≥ 2，n ∈ N）
注意：
1) [0,1,1]为最短有效斐波那契数列
```js
const _isFibonacci = array => {
    // 补全代码
    if (array.length < 3 || (array.length === 3 && array.join('') !== '001')) {
        return false
    }
    let n1 = 1
    let n2 = 1
    let sum = 1
    for (let i = 2; i < array.length;i++) {
        if (sum === array[i]) {
            sum += n1
            n1 = n2
            n2 = sum
        } else {
            return false
        }
    }
    return true
}
```
---
19. （数组扁平化）请补全JavaScript代码，要求将数组参数中的多维数组扩展为一维数组并返回该数组。
注意：
1) 数组参数中仅包含数组类型和数字类型
示例1
输入：[1,[2,[3,[4]]]]
输出：[1,2,3,4]
```js
const _flatten = arr => {
    // 补全代码
    return arr.toString().split(',').map(item => Number(item))
}
```
---
20. （数组过滤）请补全JavaScript代码，要求根据下拉框选中的条件变换重新渲染列表中展示的商品，且只展示符合条件的商品。
注意：
1) 必须使用DOM0级标准事件（onchange）
2) 建议使用ES6的filter方法
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <select name="" id="select">
            <option value="0">请选择销量范围</option>
            <option value="1">&lt100</option>
            <option value="2">100~500</option>
            <option value="3">&gt500</option>
        </select>
        <ul>
            <li>牛客logo马克杯</li>
            <li>无盖星空杯</li>
            <li>老式茶杯</li>
            <li>欧式印花杯</li>
        </ul>

        <script>
            var cups = [
                { type: 1, price: 100, color: 'black', sales: 60, name: '牛客logo马克杯' },
                { type: 2, price: 40, color: 'blue', sales: 100, name: '无盖星空杯' },
                { type: 4, price: 60, color: 'green', sales: 200, name: '老式茶杯' },
                { type: 3, price: 50, color: 'green', sales: 600, name: '欧式印花杯' }
            ]
            var select = document.querySelector('select');
            var ul = document.querySelector('ul');
            // 补全代码
            function selectContent(func) {
                let newArr = []
                let content = ''
                newArr = cups.filter(func)
                newArr.forEach(item => {
                    content += `<li>${item.name}</li>`
                })
                ul.innerHTML = content
            }
            
            select.onchange = function() {
                switch(this.selectedIndex) {
                    case 1:
                        selectContent((item) => item.sales < 100)
                        break
                    case 2:
                        selectContent((item) => item.sales >= 100 && item.sales <= 500)
                        break
                    case 3:
                        selectContent((item) => item.sales > 500)
                        break
                    default: break
                }
            }
        </script>
    </body>
</html>
```
---
21. （判断质数）请补全JavaScript代码，要求在Number对象的原型对象上添加"_isPrime"函数，该函数判断调用的对象是否为一个质数，是则返回true，否则返回false。
```js
Number.prototype._isPrime = function() {
   let num = Number(this)
   if (num > 1) {
       for(let i = 2; i < num; i++) {
           if (num % i === 0) {
               return false
           }
       }
       return true
   } else {
       return false
   }
}
```
---
22. （验证是否是身份证）请补全JavaScript代码，要求以Boolean的形式返回字符串参数是否符合身份证标准。
1) 无需考虑地区信息、出生日期、顺序码与校验码的验证
输入：_isCard('21062319980907888X')
输出：true
```js
const _isCard = number => {
    // 补全代码
    return number.toString().length === 18
}
```
---
23. 请补全JavaScript代码，要求以键/值对的对象形式返回参数数组。要求如下：
1) 键名的数据类型为Symbol
2) 键值为当前数组项
3) Symbol的描述为当前数组项
4) 返回普通对象

**注意**：每个从 [Symbol()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Symbol) 返回的 symbol 值都是唯一的。一个 symbol 值能作为对象属性的标识符；这是该数据类型仅有的目的。
```js
const _symbolKey = array => {
    // 补全代码
    let obj = {}
    array.forEach(item => {
        obj[Symbol(item)] = item
    })
    return obj
}   
```
---
24. 请补全JavaScript代码，要求以boolean的形式返回两个Set对象参数是否一样，是则返回true，否则返回false。
```js
const _isSameSet = (s1, s2) => {
    // 补全代码
    if (s1.size !== s2.size) return false
    return [...s1].every(v => s2.has(v))
}
```
---
25. （Getter）请补全JavaScript代码，完成名为"Rectangle"的矩形类。要求如下：
1) 构造函数只包含两个参数，依次为"height"、"width"
2) 设置Getter，当获取该对象的"area"属性时，返回该对象"height"与"width"属性的乘积

示例1

输入：new Rectangle(12,12).area
输出：144
```js
class Rectangle {
    // 补全代码
    constructor(height, width) {
        this.height = height
        this.width = width
    }
    
    get area() {
        return this.height * this.width
    }
}
```
---
26. 请补全代码，要求当滑动id为"range"的滑块控件时可以改变id为"rect"的矩形旋转速度。要求如下：
1. id为"rect"的矩形初始动画周期为10秒
2. id为"range"的滑块控件默认值为1、最小值为、最大值为10、滑动间隔为1
3. 当滑动滑块值为1时，矩形动画周期为10秒、当...，为...、当滑动滑块值为10时，矩形动画周期为1秒

注意：

1. 必须使用DOM0级标准事件（onchange）
2. [牛客链接](https://www.nowcoder.com/practice/5cc9c7c7021c4206ac825fda21d6a4bb?tpId=271&tags=&title=&difficulty=0&judgeStatus=0&rp=1&sourceUrl=%2Fexam%2Foj%3Fpage%3D1%26tab%3DJS%25E7%25AF%2587%26topicId%3D271)
 
**问题：这里不清楚为什么变量要加一个1，不加会导致程序无法通过，谷歌是没问题的，但是牛客上面编译出错，不知道哪里有问题？**
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
        <style type="text/css">
            #rect {
                width: 120px;
                height: 100px;
                background-color: black;
                /*补全代码*/
                animation: rect 10s linear infinite;
            }
            @keyframes rect {
                from {
                    transform: rotate(0deg);
                }
                to {
                    transform: rotate(360deg);
                }
            }
        </style>
    </head>
    <body>
        <!-- 补全代码 -->
    	<div id="rect"></div>
        <input id="range" type="range" max="10" min="1" value="1" step="1"/>
        
        <script type="text/javascript">
            // 补全代码
            // 这里不清楚为什么变量要加一个1，会导致程序无法通过，谷歌是没问题的，但是牛客上面编译出错，不知道哪里有问题
            var range1 = document.querySelector('#range') 
            var rect1 = document.querySelector('#rect')
            
            range1.onchange = function() {
                let value = this.value
                let time = 11 - value
                rect1.style.animationDuration = time + 's'
            }
        </script>
    </body>
</html>
```
---
27. 请补全JavaScript代码，要求将页面中的"p"标签以键名的形式保存在Map对象中，键名所对应的键值为该"p"标签的文字内容。
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
    </head>
    <body>
    	<p>1</p>
        <script type="text/javascript">
            const _elementKey = () => {
                // 补全代码
                let p = document.querySelector('p')
                let m = new Map()
                m.set(p, p.innerText)
                return m
            }
        </script>
    </body>
</html> 
```
---
28. 请补全JavaScript代码，实现以下效果：
1) 选中"全选"框，以下所有选项全部勾选。
2) 把"全选"框从选中状态勾选成未选中状态，其他复选框全部取消选中效果。
3) 当其他复选框全部选中，"全选框"为选中状态。
4) 当其他复选框有一个未选中，"全选框"取消选中状态。
注意：
1. 必须使用DOM0级标准事件（onchange）
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
    </head>
        <style>
            ul {
                list-style: none;
            }
        </style>
    <body>
        <ul>
            <li>全选<input type='checkbox' id='all'></li>
            <li>Java<input type='checkbox' class='item'></li>
            <li>javaScript<input type='checkbox' class='item'></li>
            <li>C++<input type='checkbox' class='item'></li>
            <li>python<input type='checkbox' class='item'></li>
            <li>.net<input type='checkbox' class='item'></li>
        </ul>

        <script>
            // 补全代码
            const all1 = document.querySelector('#all')
            const options = Array.from(document.querySelectorAll('.item'))
            
            all1.onchange = function() {
                const checked = this.checked
                options.forEach(v => v.checked = checked )
            }
            
            options.forEach(item => {
                item.onchange = function() {
                    if(!this.checked) {
                        all1.checked = false
                    } else {
                        if (options.every(v => v.checked)) {
                            all1.checked = true
                        } else {
                            all1.checked = false
                        }
                    }
                }
            })
        </script>
    </body>
</html>
```
---
29.（回文字符串）请补全JavaScript代码，要求以boolean的形式返回参数字符串是否为回文字符串。（“回文串”是一个正读和反读都一样的字符串）
```js
const _isPalindrome = string => {
    // 补全代码
    if (string === string.split('').reverse().join('')) {
        return true
    }
    return false
}
```
---
30. （proxy计时器）请补全JavaScript代码，请给参数对象添加拦截代理功能，并返回这个代理，要求每当通过代理调用该对象拥有的属性时，"count"值加1，否则减1。
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
    </head>
    <body>
    	
        <script type="text/javascript">
            let count = 0
            const _proxy = object => {
                // 补全代码
                const handler = {
                    get: (target, name) => {
                        if (target[name] === undefined) {
                            count--
                        } else {
                            count++
                        }
                        return target[name]
                    }
                }
                return new Proxy(object, handler)
            }
        </script>
    </body>
</html>
```
---
31. （proxy拦截器）请补全JavaScript代码，请给参数对象添加拦截代理功能并返回这个代理。要求如下：
1) 该函数接收多个参数，首个参数为对象，从第二个参数（包括）往后皆是该对象的属性名
2) 通过该函数给首个参数对象添加拦截器功能，每当该对象访问到该函数第二个参数（包括）往后的属性时，返回"noright"字符串，表示无权限。
```js
const _proxy = (object,...prototypes) => {
    // 补全代码
    let p = new Proxy(object, {
        get: (target, name) => {
            if (prototypes.includes(name)) return 'noright'
            return target[name]
        }
    })
    return p
}
```
---
32. 请补全JavaScript代码，要求如下：
1) 监听对象属性的变化
2) 当"person"对象的属性发生变化时，页面中与该属性相关的数据同步更新
注意：
1. 必须使用Object.defineProperty实现且触发set方法时更新视图
2. 可以使用预设代码"_render"函数
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <style>
            ul {
                list-style: none;
            }
        </style>
        <ul></ul>

        <script>
            var ul = document.querySelector('ul');
            var person = { sex: '男', age: '25', name: '王大锤', height: 28, weight: 32 };
            const _render = element => {
                var str = `<li>姓名：<span>${person.name}</span></li>
                           <li>性别：<span>${person.sex}</span></li>
                           <li>年龄：<span>${person.age}</span></li>
                           <li>身高：<span>${person.height}</span></li>
                           <li>体重：<span>${person.weight}</span></li>`
                element.innerHTML = str;
            }
            _render(ul);
            // 补全代码
            for (let key in person) {
                let value = person[key]
                Object.defineProperty(person, key, {
                    get() {
                        return value
                    },
                    set(newVal) {
                        value = newVal
                        _render(ul)
                    }
                })
            }
        </script>
    </body>
</html>
```
---
33. 请补全JavaScript代码，要求如下：
1) 当点击"-"按钮时，商品数量减1
2) 当点击"+"按钮时，商品数量加1
3) 每当点击任意按钮时，购物面板中相关信息必须同步更新
注意：
1. 必须使用DOM0级标准事件（onclick）
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
    </head>
    <body>
    	<table>
            <thead>
                <caption>
                    商品
                </caption>
            </thead>
            <tbody>
                <tr>
                    <td>炸鸡</td>
                    <td>28元</td>
                    <td><button id="zjtaiduola">-</button></td>
                    <td><span id="zjsl">0</span></td>
                    <td><button id="zjtaishaola">+</button></td>
                </tr>
                <tr>
                    <td>可乐</td>
                    <td>5元</td>
                    <td><button id="kltaiduola">-</button></td>
                    <td><span id="klsl">0</span></td>
                    <td><button id="kltaishaola">+</button></td>
                </tr>
                <tr>
                    <td>总价：</td>
                    <td><span id="total">0</span></td>
                </tr>
            </tbody>
        </table>
        
        <script type="text/javascript">
            // 补全代码
            let left1 = document.querySelector('#zjtaiduola')
            let num1 = document.querySelector('#zjsl')
            let right1 = document.querySelector('#zjtaishaola')
            
            let left2 = document.querySelector('#kltaiduola')
            let num2 = document.querySelector('#klsl')
            let right2 = document.querySelector('#kltaishaola')
            
            let total1 = document.querySelector('#total')
            function sum() {
                total1.innerText = Number(num1.innerText) * 28 + Number(num2.innerText) * 5
            }
            
            left1.onclick = function() {
                if (Number(num1.innerText) < 1) {
                    return false
                }
                num1.innerText = Number(num1.innerText) - 1
                sum()
            }
            
            right1.onclick = function() {
                num1.innerText = Number(num1.innerText) + 1
                sum()
            }
            
            left2.onclick = function() {
                if (Number(num2.innerText) < 1) {
                    return false
                }
                num2.innerText = Number(num2.innerText) - 1
                sum()
            }
            
            right2.onclick = function() {
                num2.innerText = Number(num2.innerText) + 1
                sum()
            }
            
        </script>
    </body>
</html>
```
---
34. 请补全JavaScript代码，完成函数的接口功能。要求如下：
1) 函数接收两种类型的参数，分别为"get?"和"update?name=xxx&to=yyy"，"name"、"to"为参数，"xxx"、"yyy"分别为参数对应的值。
2) 当参数为"get?"时，返回data数据
3) 当参数为"update?name=xxx&to=yyy"时，将data中所有"name"为"xxx"的项，更改为"name"值为"yyy"
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
    </head>
    <body>
    	
        <script type="text/javascript">
            let data = [
                {name: 'nowcoder1'},
                {name: 'nowcoder2'}
            ]
            
            const _api = string => {
                // 补全代码
                let [left, right] = string.split('?')
                
                if (left === 'get') {
                    return data
                } else {
                    let [name, to] = right.split('&')
                    let [a1, a2] = name.split('=')
                    let [b1, b2] = to.split('=')
                    data.forEach(v => {
                        if (v.name === a2) {
                            v.name = b2
                        }
                    })
                }
            }
        </script>
    </body>
</html>
```
---
35. （切换Tab栏目）请补全JavaScript代码，实现效果如下：
1) 当点击某个栏目（题库、面试、学习、求职）时，该栏目背景色变为'#25bb9b'，其它栏目背景色位'#fff'。
2) 当选中某个栏目时，下方内容就展示索引值相同的类名为".items"的"li"元素
注意：
1. 必须使用DOM0级标准事件（onclick）
2. 已使用自定义属性存储了栏目的索引值。点击栏目获取索引值，使用索引值控制类名为"items"下的"li"元素
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <style>
            ul {
                padding: 0;
                margin: 0;
                list-style: none;
            }

            .options li {
                float: left;
                width: 100px;
                height: 40px;
                line-height: 40px;
                text-align: center;
                border: solid 1px #ddd;
            }

            .items li {
                width: 405px;
                height: 405px;
                display: none;
                border: solid 1px #ddd;
            }
        </style>
    </head>
    <body>
        <ul class='options'>
            <li data-type="0" style='background-color: #25bb9b;'>题库</li>
            <li data-type="1">面试</li>
            <li data-type="2">学习</li>
            <li data-type="3">求职</li>
        </ul>
        <ul class='items'>
            <li style="display: block;">牛客题库，包含编程题、选择题等</li>
            <li>为你的面试提供一站式服务</li>
            <li>校招学习来牛客</li>
            <li>求职中有什么难题，可以联系我们</li>
        </ul>

        <script>
            var options = document.querySelector('.options');
            var optionItems = [].slice.call(document.querySelectorAll('.options li'));
            var items = [].slice.call(document.querySelectorAll('.items li'));
            
            // 补全代码
            options.onclick = function(e) {
                for(let i in optionItems) {
                    if (e.target === optionItems[i]) {
                        optionItems[i].style.backgroundColor = '#25bb9b'
                        items[i].style.display = 'block'
                    } else {
                        optionItems[i].style.backgroundColor = '#fff'
                        items[i].style.display = 'none'
                    }
                }
            }
        </script>
    </body>
</html>
```
---
36. （双向绑定）请补全JavaScript代码，要求如下：
1) 监听对象属性的变化
2) 当"person"对象属性发生变化时，页面中与该属性相关的数据同步更新
3) 将输入框中的值与"person"的"weight"属性绑定且当输入框的值发生变化时，页面中与该属性相关的数据同步更新
注意：
1. 必须使用Object.defineProperty实现且触发set方法时更新视图
2. 必须使用DOM0级标准事件（oninput）
3. 可以使用预设代码"_render"函数
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <style>
            ul {
                list-style: none;
            }
        </style>
        <input type="text">
        <ul></ul>

        <script>
            var ul = document.querySelector('ul');
            var person = { sex: '男', age: '25', name: '王大锤', height: 28, weight: 32 };
            var inp = document.querySelector('input');
            inp.value = person.weight;
            const _render = () => {
                var str = `<li>姓名：<span>${person.name}</span></li>
                           <li>性别：<span>${person.sex}</span></li>
                           <li>年龄：<span>${person.age}</span></li>
                           <li>身高：<span>${person.height}</span></li>
                           <li>体重：<span>${person.weight}</span></li>`
                ul.innerHTML = str;
                inp.value = person.weight;
            }
            _render(ul);
            // 补全代码
            
            function Observe(target) {
                if (typeof(target) !== 'object' || target === null) {
                    return target
                }
                
                for (let key in target) {
                    defineO(target, key, target[key])
                }
            }
            
            function defineO(target, key, value) {
                Object.defineProperty(target, key, {
                    get() {
                        return value
                    },
                    set(newVal) {
                        if(value !== newVal) {
                            value = newVal
                            _render()
                        }
                    }
                })
            }
            
            Observe(person)
            
            inp.oninput = function() {
                person.weight = this.value
            }
        </script>
    </body>
</html>
```
---
37. 请补全JavaScript代码，要求找到参数数组中出现频次最高的数据类型，并且计算出出现的次数，要求以数组的形式返回。
注意：
1) 基本数据类型之外的任何引用数据类型皆为"object"
2) 当多种数据类型出现频次相同时将结果拼接在返回数组中，出现次数必须在数组的最后

输入：__findMostType([0,0,'',''])
输出：['number','string',2]或['string','number',2]
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
    </head>
    <body>
    	
        <script type="text/javascript">
            const _findMostType = array => {
                // 补全代码
                let tem = {}
                let arr = []
                let num = 0
                for(key of array) {
                    const type = typeof key
                    if (tem[type]) {
                        tem[type]++
                    } else {
                        tem[type] = 1
                    }
                    num = tem[type] > num ? tem[type] : num
                }
                
                for (let key in tem) {
                    arr = tem[key] === num ? [...arr, key] : arr 
                }
                
                return [...arr, num]
            }
        </script>
    </body>
</html>
```
38. （字体高亮）请补全JavaScript代码，实现一个搜索字体高亮的效果。要求如下：
1) 在input框中输入要搜索的内容，当点击查询按钮时，被搜索的字体样式变为加粗，背景色变为'yellow'
2) 重新输入搜索文字，点击查询按钮时，去掉上一次的搜索效果，高亮显示效果只加在本次搜索文字上
3) 如果搜索不到相关内容，清除之前的效果
注意：
1. 需要加粗的文字请使用b标签包裹
2. 必须使用DOM0级标准事件（onclick）
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <input type="text">
        <button style="margin-right: 80px">查询</button>
        <div class="text" style="margin-top: 70px">
            牛客网隶属于北京牛客科技有限公司，牛客网成立于 2014 年 9 月，是以科技和创新驱动的教育科技公司。牛客网坚持以前沿技术服务于技术、以人工智能和大数据提升学习效率，专注探索在线教育创新模式，致力于为技术求职者提供能力提升解决方案，同时为企业级用户提供更高效的招聘解决方案，并为二者搭建桥梁，构建从学习到职业的良性生态圈。
    发展至今，牛客网在技术类求职备考、社群交流、企业招聘服务等多个垂直领域影响力均在行业中遥遥领先，产品矩阵包括IT题库、在线编程练习、线上课程、交流社区、竞赛平台、笔面试服务、ATS系统等，用户覆盖全国高校百万IT学习者并在高速增长中，同时也为京东、百度、腾讯、滴滴、今日头条、华为等200多家企业提供校园招聘、编程竞赛等线上服务，并收获良好口碑。
        </div>

        <script>
            var text = document.querySelector(".text");
            var search = document.querySelector("input");
            const btn = document.querySelector("button");
            btn.onclick = () => {
                // 补全代码
                restoreText()
                let value = search.value
                let textValue = text.innerText
                text.innerHTML = textValue.replace(new RegExp(value, 'g'), `<b style="background-color:yellow">${value}</b>`)
            }
            function restoreText() {
                let yellowLeft = `<b style="background-color:yellow">`
                let yellowRight = `</b>`
                let textHTML = text.innerHTML
                if (textHTML.indexOf(yellowLeft) !== -1) {
                     textHTML = textHTML.split(yellowLeft)
                     textHTML = textHTML.join('').split(yellowRight)
                     return textHTML.join('')   
                } else {
                    return textHTML
                }
            }
        </script>
    </body>
</html>
```
39. 请补全JavaScript代码，要求将对象参数转换为真实的DOM结构并返回。
注意：
1) tag为标签名称、props为属性、children为子元素、text为标签内容
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>

        <script>
            var vnode = {
                tag: 'ul',
                props: {
                    class: 'list'
                },
                text: '',
                children: [
                    {
                        tag: "li",
                        props: {
                            class: "item"
                        },
                        text: '',
                        children: [
                            {
                                tag: undefined,
                                props: {},
                                text: '牛客网',
                                children: []
                            }
                        ]
                    },
                    {
                        tag: "li",
                        props: {},
                        text: '',
                        children: [
                            {
                                tag: undefined,
                                props: {},
                                text: 'nowcoder',
                                children: []
                            }
                        ]
                    }
                ]
            }
            const _createElm = vnode => {
                // 补全代码
                const { tag, props, children, text } = vnode
                if (typeof(tag) === 'string') {
                    vnode.el = document.createElement(tag)
                    _setAttri(vnode.el, props)
                    vnode.el.appendChild(document.createTextNode(text))
                    children.forEach(v => vnode.el.appendChild(_createElm(v)))
                } else {
                    vnode.el = document.createTextNode(text)
                }
                return vnode.el
            }

            const _setAttri = (elem, props) => {
                for (let key in props) {
                    elem.setAttribute(key, props[key])
                }
            }
        </script>
    </body>
</html>
```
40. 查找两个节点的最近的一个共同父节点，可以包括节点自身
输入描述：
oNode1 和 oNode2 在同一文档中，且不会为相同的节点
```js
function commonParentNode(oNode1, oNode2) {
    for(;oNode1;oNode1 = oNode1.parentNode) {
        if(oNode1.contains(oNode2)) {
            return oNode1
        }
    }
}
```
41. 封装函数 f，使 f 的 this 指向指定的对象
```js
function bindThis(f, oTarget) {
    // return function() {
    //     return f.apply(oTarget, arguments)
    // }
    // return function() {
    //     return f.call(oTarget, ...arguments)
    // }
    return f.bind(oTarget)
}
```
42. 根据包名，在指定空间中创建对象
输入描述：namespace({a: {test: 1, b: 2}}, 'a.b.c.d')
输出描述：{a: {test: 1, b: {c: {d: {}}}}}
```js
function namespace(oNamespace, sPackage) {
    let arr = sPackage.split('.')
    let o = oNamespace
    arr.forEach(v => {
        if (typeof o[v] !== 'object') {
            o[v] = {}
        }
        o = o[v]
    })
    return oNamespace
}
```
43. 为 Array 对象添加一个去除重复项的方法  
输入：[false, true, undefined, null, NaN, 0, 1, {}, {}, 'a', 'a', NaN]  
输出：[false, true, undefined, null, NaN, 0, 1, {}, {}, 'a']
```js
Array.prototype.uniq = function () {
    return Array.from(new Set(this))
}
```
44. 用 JavaScript 实现斐波那契数列函数,返回第n个斐波那契数。 f(1) = 1, f(2) = 1 等
```js
function fibonacci(n) {
    if (n < 2) {
        return n
    }
    if (n >= 3) {
        let n1 = 1
        let n2 = 1
        let sum = 0
        for (let i = 2; i < n + 1; i++) {
            sum += n1
            n1 = n2
            n2 = sum
        }
        return sum
    }
}
```
45. （时间格式化输出）按所给的时间格式输出指定的时间
格式说明  
对于 2014.09.05 13:14:20  
yyyy: 年份，2014  
yy: 年份，14  
MM: 月份，补满两位，09  
M: 月份, 9  
dd: 日期，补满两位，05  
d: 日期, 5  
HH: 24制小时，补满两位，13  
H: 24制小时，13  
hh: 12制小时，补满两位，01  
h: 12制小时，1  
mm: 分钟，补满两位，14  
m: 分钟，14  
ss: 秒，补满两位，20  
s: 秒，20  
w: 星期，为 ['日', '一', '二', '三', '四', '五', '六'] 中的某一个，本 demo 结果为 五  
输入：formatDate(new Date(1409894060000), 'yyyy-MM-dd HH:mm:ss 星期w')  
输出：2014-09-05 13:14:20 星期五  
```js
function formatDate(date, format) {
    const addZero = (data) => {
        if (data < 10) {
            return '0' + data
        }
        return data
    }
    let obj = {
        'yyyy': date.getFullYear(),
        'yy': date.getFullYear() % 100,
        'MM': addZero(date.getMonth() + 1),
        'M': date.getMonth() + 1,
        'dd': addZero(date.getDate()),
        'd': date.getDate(),
        'HH': addZero(date.getHours()),
        'H': date.getHours(),
        'hh': addZero(date.getHours() % 12),
        'h': date.getHours() % 12,
        'mm': addZero(date.getMinutes()),
        'm': date.getMinutes(),
        'ss': addZero(date.getSeconds()),
        's': date.getSeconds(),
        'w': () => {
            day = ['日', '一', '二', '三', '四', '五', '六']
            return day[date.getDay()]
        }
    }
    
    for (let key in obj) {
        format = format.replace(key, obj[key])
    }
    return format
}
```
46. （获取字符串的长度）如果第二个参数 bUnicode255For1 === true，则所有字符长度为 1，
否则如果字符 Unicode 编码 > 255 则长度为 2  
输入：'hello world, 牛客', false  
输出：17
```js
function strLength(s, bUnicode255For1) {
    let len = s.length
    if (!bUnicode255For1) {
        for (let i in s) {
            if (s.charCodeAt(i) > 255) len++
        }
    }
    return len
}
```
47. （邮箱字符串判断）判断输入是否是正确的邮箱格式  
输入描述：  
邮箱字符串  
输出描述：  
true表示格式正确
```js
function isAvailableEmail(sEmail) {
    var reg = /^([\w+\.])+@\w+([.]\w+)+$/
    return reg.test(sEmail)
}
```
48. （计数）统计数组 arr 中值等于 item 的元素出现的次数  
输入：[1, 2, 4, 4, 3, 4, 3], 4  
输出：3 
```js
function count(arr, item) {
    return arr.filter(v => v === item).length
}
```
49. （查找重复元素）找出数组 arr 中重复出现过的元素（不用考虑返回顺序）  
输入：[1, 2, 4, 4, 3, 3, 1, 5, 3]  
输出：[1, 3, 4]
```js
function duplicates(arr) {
    let temp = []
    arr.forEach(elem => {
        if (arr.indexOf(elem) !== arr.lastIndexOf(elem) && temp.indexOf(elem) === -1) {
            temp.push(elem)
        }
    })
    return temp
}
```
50. （计时器）实现一个打点计时器，要求  
1、从 start 到 end（包含 start 和 end），每隔 100 毫秒 console.log 一个数字，每次数字增幅为 1  
2、返回的对象中需要包含一个 cancel 方法，用于停止定时操作  
3、第一个数需要立即输出  
```js
function count(start, end) {
    console.log(start)
    let time = setInterval(() => {
        if (start < end) {
            console.log(++start)
        } else {
            clearInterval(time)
        }
    }, 100)
    return {
        cancel() {
            clearInterval(time)
        }
    }
}
```
51. （流程控制）实现 fizzBuzz 函数，参数 num 与返回值的关系如下：  
1、如果 num 能同时被 3 和 5 整除，返回字符串 fizzbuzz  
2、如果 num 能被 3 整除，返回字符串 fizz  
3、如果 num 能被 5 整除，返回字符串 buzz  
4、如果参数为空或者不是 Number 类型，返回 false  
5、其余情况，返回参数 num  
输入：15  
输出：fizzbuzz
```js
function fizzBuzz(num) {
    if (typeof num === 'number' && num) {
        if (!(num % 3 ) && !(num % 5)) return 'fizzbuzz'
        if (!(num % 3)) return 'fizz'
        if (!(num % 5)) return 'buzz'
        return num
    } else {
        return false
    }
}
```
52. （函数传参）将数组 arr 中的元素作为调用函数 fn 的参数
```js
function argsAsArray(fn, arr) {
    return fn.apply(this, arr)
}
```
53. （函数的上下文）将函数 fn 的执行上下文改为 obj 对象  
输入：function () {return this.greeting + ', ' + this.name + '!!!';}, {greeting: 'Hello', name: 'Rebecca'}  
输出：Hello, Rebecca!!!
```js
function speak(fn, obj) {
    return fn.apply(obj)
}
```
54. （返回函数）实现函数 functionFunction，调用之后满足如下条件：  
1、返回值为一个函数 f  
2、调用返回的函数 f，返回值为按照调用顺序的参数拼接，拼接字符为英文逗号加一个空格，即 ', '  
3、所有函数的参数数量为 1，且均为 String 类型  
functionFunction('Hello')('world')
输出：Hello, world
```js
function functionFunction(str) {
    let f = function(s) {
        return str + ', ' + s
    }
    return f
}
```
55. （使用闭包）实现函数 makeClosures，调用之后满足如下条件：  
1、返回一个函数数组 result，长度与 arr 相同  
2、运行 result 中第 i 个函数，即 result[i]()，结果与 fn(arr[i]) 相同  

示例： 
```js
var arr = [1,2,3];
var fn = function (x) {
    return x * x;
}
var result = makeClosures(arr,fn);
(result[1]() === 4) === (fn(arr[1]) === 4) === true
```
解答：
```js
function makeClosures(arr, fn) {
    let result = []
    if (arr.length) {
        arr.forEach((v, i) => {
            result.push(fn.bind(this, arr[i]))
        })
    }
    return result
}
```
56. （二次封装函数）已知函数 fn 执行需要 3 个参数。请实现函数 partial，调用之后满足如下条件：  
1、返回一个函数 result，该函数接受一个参数  
2、执行 result(str3) ，返回的结果与 fn(str1, str2, str3) 一致  
输入：var sayIt = function(greeting, name, punctuation) {     return greeting + ', ' + name + (punctuation || '!'); };  partial(sayIt, 'Hello', 'Ellie')('!!!');  
输出：Hello, Ellie!!!
```js
function partial(fn, str1, str2) {
    return function(str3) {
        return fn(str1, str2, str3)
    }
}
```
57. （使用 arguments）函数 useArguments 可以接收 1 个及以上的参数。请实现函数 useArguments，返回所有调用参数相加后的结果。本题的测试参数全部为 Number 类型，不需考虑参数转换。  
输入：1, 2, 3, 4  
输出：10  
```js
function useArguments() {
    return [...arguments].reduce((a, b) => a + b)
}
```
58. （使用 apply 调用函数）实现函数 callIt，调用之后满足如下条件  
1、返回的结果为调用 fn 之后的结果  
2、fn 的调用参数为 callIt 的第一个参数之后的全部参数  
```js
function callIt(fn) {
    return fn.apply(this, [].slice.call(arguments, 1))
}
```
59. （二次封装函数）实现函数 partialUsingArguments，调用之后满足如下条件：  
1、返回一个函数 result  
2、调用 result 之后，返回的结果与调用函数 fn 的结果一致  
3、fn 的调用参数为 partialUsingArguments 的第一个参数之后的全部参数以及 result 的调用参数  
```js
function partialUsingArguments(fn) {
    let args1 = Array.prototype.slice.call(arguments, 1)
    return function() {
        let arg2 = Array.prototype.slice.call(arguments, 0)
        return fn.apply(this, args1.concat(arg2))
    }
}
```
60. （模块）完成函数 createModule，调用之后满足如下要求：
1、返回一个对象
2、对象的 greeting 属性值等于 str1， name 属性值等于 str2
3、对象存在一个 sayIt 方法，该方法返回的字符串为 greeting属性值 + ', ' + name属性值
```js
function createModule(str1, str2) {
    return {
        greeting: str1,
        name: str2,
        sayIt: function() {
            return this.greeting + ', ' + this.name
        }
    }
}
```
61. （二进制转换）获取数字 num 二进制形式第 bit 位的值。注意：  
1、bit 从 1 开始  
2、返回 0 或 1  
3、举例：2 的二进制为 10，第 1 位为 0，第 2 位为 1  
```js
function valueAtBit(num, bit) {
    let number = num.toString(2)
    return number[number.length - bit]
}
```
62. （二进制转换）给定二进制字符串，将其换算成对应的十进制数字  
输入：'11000000'  
输出：192
```js
function base10(str) {
    return parseInt(str, 2)
}
```
63. （二进制转换）将给定数字转换成二进制字符串。如果字符串长度不足 8 位，则在前面补 0 到满8位。
```js
function convertToBinary(num) {
    let number = num.toString(2)
    while(number.length < 8) {
        number = '0' + number
    }
    return number
} 
```
64. （乘法）求 a 和 b 相乘的值，a 和 b 可能是小数，需要注意结果的精度问题  
输入：3, 0.0001  
输出：0.0003
```js
function multiply(a, b) {
    let arr1 = a.toString().split('.')
    let arr2 = b.toString().split('.')
    let length = Math.max(arr1[1] ? arr1[1].length : 0, arr2[1] ? arr2[1].length : 0)
    let s = (a * b).toFixed(length)
    return s
}
```
65. （改变上下文）将函数 fn 的执行上下文改为 obj，返回 fn 执行后的值
```js
function alterContext(fn, obj) {
    return fn.call(obj)
}
```
66. （批量改变对象的属性）给定一个构造函数 constructor，请完成 alterObjects 方法，将 constructor 的所有实例的 greeting 属性指向给定的 greeting 变量。  
输入：  
var C = function(name) {this.name = name; return this;}; 
var obj1 = new C('Rebecca'); 
alterObjects(C, 'What\'s up'); obj1.greeting;  
输出：What's up
```js
function alterObjects(constructor, greeting) {
    constructor.prototype.greeting = greeting
}
```
67. （属性遍历）找出对象 obj 不在原型链上的属性(注意这题测试例子的冒号后面也有一个空格~)  
1、返回数组，格式为 key: value  
2、结果数组不要求顺序  
输入：  
var C = function() {this.foo = 'bar'; this.baz = 'bim';};   
C.prototype.bop = 'bip';   
iterate(new C());  
输出：["foo: bar", "baz: bim"]
```js
function iterate(obj) {
    let arr = []
    Object.keys(obj).forEach(key => {
        arr.push(`${key}: ${obj[key]}`)
    })
    return arr
}
```
68. （判断是否包含数字）给定字符串 str，检查其是否包含数字，包含返回 true，否则返回 false  
输入：'abc123'  
输出：true
```js
function containsNumber(str) {
    const reg = /([0-9])/
    return reg.test(str)
}
```
69. （检查重复字符串）给定字符串 str，检查其是否包含连续重复的字母（a-zA-Z），包含返回 true，否则返回 false  
输入：'rattler'  
输出： true
```js
function containsRepeatingLetter(str) {
    return /([a-zA-Z])\1/.test(str)
}
```
70. （判断是否以元音字母结尾）给定字符串 str，检查其是否以元音字母结尾  
1、元音字母包括 a，e，i，o，u，以及对应的大写  
2、包含返回 true，否则返回 false  
输入：'gorilla'  
输出：true  
```js
function endsWithVowel(str) {
    let arr = ['a', 'e', 'i', 'o', 'u']
    return arr.indexOf(str[str.length - 1].toLowerCase()) !== -1
}
```
71. （获取指定字符串）给定字符串 str，检查其是否包含 连续3个数字，请使用正则表达式实现。  
1、如果包含，返回最先出现的 3 个数字的字符串  
2、如果不包含，返回 false
输入：'9876543'  
输出：987
```js
function captureThreeNumbers(str) {
    var result = str.match(/(\d{3})/)
    return result ? result[0] : false
}
```
72. 给定字符串 str，检查其是否符合如下格式  
1、XXX-XXX-XXXX  
2、其中 X 为 Number 类型  
输入：'800-555-1212'  
输出：true
```js
function matchesPattern(str) {
    return (/^\d{3}\-\d{3}\-\d{4}$/).test(str)
}
```
73. （判断是否符合指定格式）给定字符串 str，检查其是否符合如下格式  
1、XXX-XXX-XXXX  
2、其中 X 为 Number 类型  
输入：'800-555-1212'  
输出：true  
```js
function matchesPattern(str) {
    let reg = /^(\d{3}\-){2}\d{4}$/
    return reg.test(str)
}
```
74. （判断是否符合 USD 格式）给定字符串 str，检查其是否符合美元书写格式  
1、以 $ 开始  
2、整数部分，从个位起，满 3 个数字用 , 分隔  
3、如果为小数，则小数部分长度为 2  
4、正确的格式如：$1,023,032.03 或者 $2.03，错误的格式如：$3,432,12.12 或者 $34,344.3  
输入：'$20,933,209.93'  
输出：true
```js
function isUSD(str) {
    let reg = /^[$]([1-9]\d{0,2})((,\d{3})*?)(\.\d{2})?$/
    return reg.test(str)
}
```
75. （颜色字符串转换）将 rgb 颜色字符串转换为十六进制的形式，如 rgb(255, 255, 255) 转为 #ffffff
1) rgb 中每个 , 后面的空格数量不固定  
2) 十六进制表达式使用六位小写字母  
3) 如果输入不符合 rgb 格式，返回原始输入  
输入：'rgb(255, 255, 255)'  
输出：#ffffff
```js
function rgb2hex(sRGB) {
     let reg = /^rgb\((\d{1,3})\, *(\d{1,3})\, *(\d{1,3})\)$/
     let arr = sRGB.match(reg)
     if (arr) {
         let str = '#'
         arr.forEach((v, i) => {
             if (i > 0) {
                 let item = Number(v).toString(16)
                 if (item.length < 2) {
                     item = '0' + item
                 }
                 str += item
             }
         })
         return str
     }
     return sRGB 
}
```
76. （将字符串转换为驼峰格式）css 中经常有类似 background-image 这种通过 - 连接的字符，通过 javascript 设置样式的时候需要将这种样式转换成 backgroundImage 驼峰格式，请完成此转换功能  
1) 以 - 为分隔符，将第二个起的非空单词首字母转为大写  
2) -webkit-border-image 转换后的结果为 webkitBorderImage  
输入：'font-size'  
输出：fontSize
```js
function cssStyle2DomStyle(sName) {
    let reg = /-([a-z])/g
    return sName.replace(reg, function(fullMatch, g, i) {
        if (i === 0) return g
        return g.toUpperCase()
    })
}
```
77. （购物车）HTML模块为一个简化版的购物车，tbody为商品列表，tfoot为统计信息，系统会随机在列表中生成一些初始商品信息  
1、请完成add函数，在列表后面显示items商品信息。参数items为{name: String, price: Number}组成的数组  
2、请完成bind函数，点击每一行的删除按钮(包括通过add增加的行)，从列表中删除对应行  
3、请注意同步更新统计信息，价格保留小数点后两位  
4、列表和统计信息格式请与HTML示例保持一致  
5、不要直接手动修改HTML中的代码  
6、不要使用第三方库  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<style>
    body,html{
    padding: 0;
    margin: 0;
    font-size: 14px;
    color: #000000;
}
table{
    border-collapse: collapse;
    width: 100%;
    table-layout: fixed;
}
thead{
    background: #3d444c;
    color: #ffffff;
}
td,th{
    border: 1px solid #e1e1e1;
    padding: 0;
    height: 30px;
    line-height: 30px;
    text-align: center;
}
</style>
<body>
    <table id="jsTrolley">
        <thead><tr><th>名称</th><th>价格</th><th>操作</th></tr></thead>
        <tbody>
            <tr><td>产品1</td><td>10.00</td><td><a href="javascript:void(0);">删除</a></td></tr>
            <tr><td>产品2</td><td>30.20</td><td><a href="javascript:void(0);">删除</a></td></tr>
            <tr><td>产品3</td><td>20.50</td><td><a href="javascript:void(0);">删除</a></td></tr>
        </tbody>
        <tfoot><tr><th>总计</th><td colspan="2">60.70(3件商品)</td></tr></tfoot>
    </table>
</body>
</html>
<script>
function add(items) {
        let tbody = document.querySelector('tbody')

        items.forEach(v => {
            let tr = document.createElement('tr');
        tr.innerHTML = `<td>${v.name}</td><td>${Number(v.price).toFixed(2)}</td><td><a href="javascript:void(0);">删除</a></td>`
            tbody.appendChild(tr)
        })

        totalPrice()
}
function totalPrice() {
       let tbody = document.getElementsByTagName('tbody')[0];
       let trList = tbody.children;
       let total = 0;
       for(let j=0;j<trList.length;j++){
           total += parseFloat(trList[j].children[1].innerHTML);
       
       }
        document.getElementsByTagName('tfoot')[0].childNodes[0].children[1].innerHTML = total.toFixed(2)+"("+trList.length+'件商品)';
}

function bind() {
    let tbody = document.querySelector('tbody')

    tbody.addEventListener('click', (e) => {
        if (e.target.innerText === '删除') {
            e.target.parentNode.parentNode.remove()
            totalPrice()
        }
    })
}
</script>
```
78. （表格排序）系统会在tbody中随机生成一份产品信息表单，如html所示。  
请完成 sort 函数，根据参数的要求对表单所有行进行重新排序。
1、type为id、price或者sales，分别对应第1 ~ 3列  
2、order为asc或者desc，asc表示升序，desc为降序  
3、例如 sort('price', 'asc') 表示按照price列从低到高排序  
4、所有表格内容均为数字，每一列数字均不会重复  
5、不要使用第三方插件  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<style>
    body,html{
    padding: 0;
    margin: 0;
    font-size: 14px;
    color: #000000;
}
table{
    border-collapse: collapse;
    width: 100%;
    table-layout: fixed;
}
thead{
    background: #3d444c;
    color: #ffffff;
}
td,th{
    border: 1px solid #e1e1e1;
    padding: 0;
    height: 30px;
    line-height: 30px;
    text-align: center;
}
</style>
<body>
    <table>
        <thead>
            <tr><th>id</th><th>price</th><th>sales</th></tr>
        </thead>
        <tbody id="jsList">
            <tr><td>1</td><td>10.0</td><td>800</td></tr>
            <tr><td>2</td><td>30.0</td><td>600</td></tr>
            <tr><td>3</td><td>20.5</td><td>700</td></tr>
            <tr><td>4</td><td>40.5</td><td>500</td></tr>
            <tr><td>5</td><td>60.5</td><td>300</td></tr>
            <tr><td>6</td><td>50.0</td><td>400</td></tr>
            <tr><td>7</td><td>70.0</td><td>200</td></tr>
            <tr><td>8</td><td>80.5</td><td>100</td></tr>
        </tbody>
    </table>
</body>
</html>
<script>
    // order => asc, desc
    function sort(type, order) {
        if (type && order) {
            let tbody = document.querySelector('#jsList')
            let typeNum = type === 'id' ? 0 : type === 'price' ? 1 : type === 'sales' ? 2 : null
            let len = tbody.children.length
            let items = []
            for (let i = 0; i < len; i++) {
                items.push(tbody.children[i])
            }
            items = items.sort((a, b) => order === 'desc' ? (b.children[typeNum].innerHTML - a.children[typeNum].innerHTML) : (a.children[typeNum].innerHTML - b.children[typeNum].innerHTML))
            for (let key of items) {
                tbody.appendChild(key)
            }
        }
    }
    sort('price', 'desc')
</script>
```
79. （替换链接）页面中存在id=jsContainer的DOM元素。
该DOM元素内会给出一段随机文本，可能包含一些链接，比如https://www.baidu.com，或者 www.baidu.com?from=onlineExam，如果出现链接文本，请给该链接文本加上链接标签，用户点击后能直接在新窗口中打开该链接。  
请完成 link 函数，完成该功能  
1、container只有纯文本内容，不包含其他dom元素  
2、识别所有以http://、https://或者www.开始的链接  
3、所有www.开头的链接，默认使用 http 协议  
4、所有链接在新窗口打开  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<style>

</style>
<body>
    <div id="jsContainer">
        这里会给出一段随机文本，可能包含一些链接，比如https://www.baidu.com，或者 www.baidu.com?from=onlineExam，如果出现链接文本，请给该链接文本加上链接标签，用户点击后能直接在新窗口中打开该链接。
    </div>
</body>
</html>
<script>
    function link() {
        let tbody = document.querySelector('#jsContainer')
        tbody.innerHTML = tbody.innerText.replace(/(http(s)?:\/\/|w{3}\.)[\w\.\?\=&%#]+/g, $1=>{
        return `<a href="${/^w{3}/.test($1) ? 'http://' + $1 : $1}" target="_blank">${$1}</a>`
        })
    }
</script>
```
80. （倒计时）倒计时是web开发中常见的组件，请完成second和render两个函数，完成倒计时的显示部分  
1、second函数的输入为整数，返回{day: Int, hour: Int, min: Int, second: Int}  
2、render函数的输入为second函数的输出，将数据在页面对应的DOM元素上显示出来，格式如html所示  
3、如果day为0，隐藏对应的DOM元素，否则显示（请直接使用已经实现的css代码）  
4、数值不足两位，前面补充0  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<style>
.hide{
	display: none;
}
</style>
<body>
    <div id="jsCountdown">
        <span>01天</span>
        <span>02:</span>
        <span>03:</span>
        <span>04</span>
    </div>
</body>
</html>
<script>
render(second(3601))
function second(second) {
    let sec = 1
    let min = 60 * sec
    let hour = 60 * min
    let day = 24 * hour
    let str = {
        day: parseInt(second / day),
        hour: parseInt(second % day / hour),
        min: parseInt(second % hour / min),
        second: second % min
    }
    return str
}

function render(data) {
    console.log(data)
    let tbody = document.querySelector('#jsCountdown')
    const len2 = (d) => {
        d = '0' + d
        return d.match(/\d{2}$/)
    }
    const c = `
        <span class="${data.day === 0 ? 'hide' : ''}">${len2(data.day)}天</span>
        <span>${len2(data.hour)}:</span>
        <span>${len2(data.min)}:</span>
        <span>${len2(data.second)}</span>
    `
    tbody.innerHTML = c
}
</script>
```
81. （双色球机选一注）双色球由33个红球和16个蓝球组成，1注双色球包括6个不重复的红球和1个蓝球。  
请阅读给出的页面和代码，完成 randomFn 函数，实现“随机一注”功能，要求如下：  
函数返回：  
  1.以字符串形式输出“随机一注”结果，选中的红蓝球用"|"隔开，红球在前，号码间用半角逗号隔开，如"06,10,13,18,23,27|05"  
  2.红球和蓝球号码排列顺序 需与页面展示的顺序对应  
页面交互：  
  1.将选中的红球和蓝球（页面中对应DOM元素）用class="active"高亮  
  2.将选中的球按号码从小到大排列，移至所属组的前方，结果如示意图所示  
  3.每次执行 randomFn 函数，输出符合要求且不完全重复  
  
注意：  
1、请使用原生JavaScript操作DOM元素，不要增加、删除DOM元素或修改css  
2、请使用ES5语法  
3、答题时不要使用第三方插件  
4、运行浏览器为chrome浏览器  
5、  
// 可能涉及的点  

// element.className  
// element.classList  
// element.classList.add  
// element.classList.remove  
// element.getAttribute  
// element.setAttribute  
// element.innerHTML  
// element.insertBefore 
// element.parentNode    
  
// document.querySelector  
// document.querySelectorAll  
// document.getElementsByTagName  
// document.getElementsByClassName  
  
// Array.sort  
// Array.push  
// Array.join  
// Array.indexOf  
// Array.forEach  
// Array.map  
  
// Math.random  
// Math.floor  
  
// Number.toString()  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<style>
.main .balls {
    width: 450px;
    padding: 30px 10px 10px;
    margin-bottom: 20px;
    position: relative;
    border-radius: 4px;
}

.main .balls:after {
    content: '\20';
    clear: both;
    display: block;
    height: 0;
    overflow: hidden;
}

.main .balls span {
    position: absolute;
    left: 12px;
    top: 5px;
    font-size: 13px;
}

.main b {
    float: left;
    width: 30px;
    height: 30px;
    font-size: 15px;
    background: #FFF;
    border: 1px solid;
    border-radius: 50%;
    line-height: 30px;
    text-align: center;
    margin-right: 8px;
    margin-bottom: 8px;
    cursor: pointer;
}

.main .red .active {
    background: #f56c6c;
    color: #FFF;
}

.main .blue .active {
    background: #3a8ee6;
    color: #FFF;
}

.main .red {
    background: #feeff0;
}

.main .red b {
    border-color: #f56c6c;
}

.main .blue {
    background: #ecf8ff;
}

.main .blue b {
    border-color: #3a8ee6;
}
</style>
<body>
    <div class="main">
        <div class="balls red">
            <span>红球</span>
            <div class="balls-wp">
                <b>01</b>
                <b>02</b>
                <b>03</b>
                <b>04</b>
                <b>05</b>
                <b>06</b>
                <b>07</b>
                <b>08</b>
                <b>09</b>
                <b>10</b>
                <b>11</b>
                <b>12</b>
                <b>13</b>
                <b>14</b>
                <b>15</b>
                <b>16</b>
                <b>17</b>
                <b>18</b>
                <b>19</b>
                <b>20</b>
                <b>21</b>
                <b>22</b>
                <b>23</b>
                <b>24</b>
                <b>25</b>
                <b>26</b>
                <b>27</b>
                <b>28</b>
                <b>29</b>
                <b>30</b>
                <b>31</b>
                <b>32</b>
                <b>33</b>
            </div>
        </div>
        <div class="balls blue">
            <span>蓝球</span>
            <div class="balls-wp">
                <b>01</b>
                <b>02</b>
                <b>03</b>
                <b>04</b>
                <b>05</b>
                <b>06</b>
                <b>07</b>
                <b>08</b>
                <b>09</b>
                <b>10</b>
                <b>11</b>
                <b>12</b>
                <b>13</b>
                <b>14</b>
                <b>15</b>
                <b>16</b>
            </div>
        </div>
    </div>
</body>
</html>
<script>
randomFn();

function randomFn() {
    return selectBalls('red', 6) + '|' + selectBalls('blue', 1)
}

function selectBalls(color, n) {
    const wrap = document.querySelector('.' + color + ' .balls-wp')
    const balls = wrap.getElementsByTagName('b')
    for (let i = 0; i < n; i++) {
        balls[i].classList.remove('active')
    }
    let choosed = []
    for (let i = 0; i < n; i++) {
        const index = Math.floor(Math.random() * balls.length)
        choosed.push(balls[index])
        balls[index].classList.add('active')
        balls[index].remove()
    }

    choosed.sort((a, b) => {
        return a.textContent - b.textContent
    })

    for (let i = n - 1; i >= 0; --i) {
        wrap.insertBefore(choosed[i], balls[0])
    }

    return choosed.map(val => {
        return val.textContent
    }).join(',')
}

</script>
```
82. （智能提示）
本题展示了一个简化版的搜索框智能提示功能，请按照如下要求完成suggest函数。  
1、当输入框的值发生变化时，系统会调用suggest函数，用于显示/隐藏智能提示数据，参数items为一个字符串数组。  
2、当items中的字符串和输入框的值匹配时，将匹配的数据依次渲染在ul下的li节点中，并显示.js-suggest节点，否则移除ul下的所有li节点，并隐藏.js-suggest节点  
3、输入框的值需要移除两侧空白再进行匹配  
4、输入框的值为空时，按照全部不匹配处理  
5、字符串使用模糊匹配，比如"北大"能匹配"北大"和"北京大学"，但不能匹配"大北京"，即按照 /北.*?大.*?/ 这个正则进行匹配  
6、通过在.js-suggest节点上添加/移除 hide 这个class来控制该节点的隐藏/显示  
7、当前界面是执行 suggest(['不匹配数据', '根据输入框的值', '从给定字符串数组中筛选出匹配的数据，依次显示在li节点中', '如果没有匹配的数据，请移除所有li节点，并隐藏.js-suggest节点']) 后的结果  
8、请不要手动修改html和css  
9、不要使用第三方插件  
10、请使用ES5语法  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <title>Document</title>
</head>
<style>
.search{
    position: relative;
}
.js-input{
    width: 450px;
    height: 22px;
    line-height: 22px;
    font-size: 16px;
    padding: 8px;
    border: 1px solid #cccccc;
    outline: none;
}
.js-suggest{
    width: 466px;
    font-size: 14px;
    border: 1px solid #cccccc;
    background: #ffffff;
    position: absolute;
    left: 0;
    top: 39px;
}
.js-suggest.hide{
    display: none;
}
.js-suggest ul{
    display: block;
    list-style: none;
    padding: 0;
    margin: 0;
}
.js-suggest ul li{
    color: #000;
    font: 14px arial;
    line-height: 25px;
    padding: 0 8px;
    position: relative;
    cursor: default;
}
.js-suggest ul li:hover{
    background: #f0f0f0;
}
</style>
<body>
    <div class="search">
        <div><input type="text" class="js-input" value="的"></div>
        <div class="js-suggest">
            <ul>
                <li>根据输入框的值</li>
                <li>从给定字符串数组中筛选出匹配的数据，依次显示在li节点中</li>
                <li>如果没有匹配的数据，请移除所有li节点，并隐藏.js-suggest节点</li>
            </ul>
        </div>
    </div>
</body>
</html>
<script>
function suggest(items) {
    const val = document.querySelector('.js-input').value.trim()
    const reg = new RegExp(val.split('').map(v => `${safeFilter(v)}.*?`).join(''))
    items = items.filter(v => val !== '' && reg.test(v))
    document.querySelector('.js-suggest').classList[items.length ? 'remove' : 'add']('hide')
    document.querySelector('.js-suggest').children[0].innerHTML = `${ items.map(v => `<li>${v}</li>`).join('') }`
}

function safeFilter(str) {
    return '()[]+*?'.indexOf(str) !== -1 ? `\\${str}` : str
}
</script>
```
83. （文字输出）页面上存在id为jsBlink的下划线闪动节点，请按照如下需求实现 output 函数  
1、函数 output 接收一个字符串参数，每隔200毫秒在闪动节点之前逐个显示字符  
2、请新建span节点放置每个字符，其中span必须存在class "word"，并随机加上 color1 ~ color24 中的任一个class（请使用系统随机函数）  
3、每次输出指定字符串前，请将闪动节点之前的所有其他节点移除  
4、不要销毁或者重新创建闪动节点  
5、如果输出字符为空格、<、>，请分别对其进行HTML转义，如果是\n请直接输出<br />，其他字符不需要做处理  
6、请不要手动调用output函数  
7、当前界面为系统执行 output('hello world\n你好世界') 之后，最终的界面，过程请参考以下图片  
8、请不要手动修改html和css  
9、不要使用第三方插件  
10、请使用ES5语法  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <title>Document</title>
</head>
<style>
html, body {margin: 0;}
.color1 {color: #E60012;}
.color2 {color: #EB6100;}
.color3 {color: #F39800;}
.color4 {color: #FCC800;}
.color5 {color: #FFF100;}
.color6 {color: #CFDB00;}
.color7 {color: #8FC31F;}
.color8 {color: #22AC38;}
.color9 {color: #009944;}
.color10 {color: #009B6B;}
.color11 {color: #009E96;}
.color12 {color: #00A0C1;}
.color13 {color: #00A0E9;}
.color14 {color: #0086D1;}
.color15 {color: #0068B7;}
.color16 {color: #00479D;}
.color17 {color: #1D2088;}
.color18 {color: #601986;}
.color19 {color: #920783;}
.color20 {color: #BE0081;}
.color21 {color: #E4007F;}
.color22 {color: #E5006A;}
.color23 {color: #E5004F;}
.color24 {color: #E60033;}
.word {font-size: 20px;}
.content {text-align: center;font-size:0;}
.blink {
    font-size: 20px;
    animation: fade 500ms infinite;
    -webkit-animation: fade 500ms infinite;
}
@keyframes fade {
    from {opacity: 1.0;}
    50% {opacity: 0;}
    to {opacity: 1.0;}
}
</style>
<body>
    <div class="content">
        <span class="word color23">h</span>
        <span class="word color22">e</span>
        <span class="word color4">l</span>
        <span class="word color24">l</span>
        <span class="word color17">o</span>
        <span class="word color2">&nbsp;</span>
        <span class="word color9">w</span>
        <span class="word color3">o</span>
        <span class="word color1">r</span>
        <span class="word color23">l</span>
        <span class="word color15">d</span>
        <br>
        <span class="word color15">你</span>
        <span class="word color13">好</span>
        <span class="word color16">世</span>
        <span class="word color19">界</span>
        <span class="blink" id="jsBlink">|</span>
    </div>
</body>
</html>
<script>
function output(str) {
    const contents = document.getElementsByClassName('content')
    const jsBlink = document.getElementById('jsBlink')
    let childs = contents[0].childNodes
    while(childs.length > 0) {
        if (childs[0] === jsBlink) { break }
        contents[0].removeChild(childs[0])
    }
    let i = 0
    let interval = setInterval(() => {
        if (i === str.length) clearInterval(interval)
        else {
            let c = str[i]
            if (c === '\n') {
                const br = document.createElement('br')
                contents[0].insertBefore(br, jsBlink)
            } else {
                let newSpan = document.createElement('span')
                newSpan.className = 'word color' + (Math.floor(Math.random() * 24) + 1)
                if (c == '<') {
                    c = '&lt'
                } else if (c == '>') {
                    c = '&gt'
                } else if (c == ' ') {
                    c = '&nbsp'
                }
                newSpan.innerHTML = c
                contents[0].insertBefore(newSpan, jsBlink)
            }
            i++
        }
    }, 200)
}
</script>
```
84. （分页）本题展示了一个分页组件，界面中存在id=jsContainer的节点A，系统会随机实例化各种Pagination实例，请按照如下要求补充完成Pagination函数。  
1、最多连续显示5页，居中高亮显示current页（如demo1所示)  
2、total <= 1 时，隐藏该组件（如demo2所示）  
3、如果total<=5，则显示全部页数，隐藏“首页”和“末页”元素（如demo3所示）  
4、当current居中不足5页，向后(前)补足5页，隐藏“首页”(“末页”)元素(如demo4和demo5所示)  
5、total、current均为正整数，1 <= current <= total  
6、当前界面中，节点A为系统执行 new Pagination(节点A，20, 10) 后的展示效果  
7、请不要手动修改html和css  
8、不要使用第三方插件  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <title>Document</title>
</head>
<style>
.demo{
    margin-bottom: 20px;
    border: 1px solid #ebedf0;
    border-radius: 2px;
    padding: 10px;
}
.demo div{
    margin-bottom: 10px;
    font-size: 14px;
}

.pagination{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    font-size: 14px;
    line-height: 1.5;
    list-style: none;
    display: inline-block;
}
.pagination.hide{
    display: none;
}
.pagination li{
    position: relative;
    display: inline-block;
    float: left;
    height: 32px;
    margin: 0;
    padding: 0 15px;
    line-height: 30px;
    background: #fff;
    border: 1px solid #d9d9d9;
    border-top-width: 1.02px;
    border-left: 0;
    cursor: pointer;
    transition: color 0.3s, border-color 0.3s;
}
.pagination li:first-child{
    border-left: 1px solid #d9d9d9;
    border-radius: 4px 0 0 4px;
}
.pagination li:last-child{
    border-radius: 0 4px 4px 0;
}
.pagination li:first-child{
    box-shadow: none !important;
}
.pagination li.current{
    border-color: #1890ff;
    color: #1890ff;
    border-left: 1px solid #1890ff;
}
.pagination li.current:not(:first-child) {
    margin-left: -1px;
}
</style>
<body>
    <div id="jsContainer">
        
    </div>
</body>
</html>
<script>
function Pagination(container, total, current) {
    this.total = total;
    this.current = current;
    this.html = html;
    this.val = val;
    this.el = document.createElement('ul')//TODO: 创建分页组件根节点
    this.el.className = 'pagination'
    if (!this.el) return;

    this.el.innerHTML = this.html();
    container.appendChild(this.el);
    this.el.className = total <= 1 ? 'pagination hide' : 'pagination' //TODO: 判断是否需要隐藏当前元素

    function html() {
        if (this.total <= 1) return '';
        let ul = ''
        //TODO: 生成组件的内部html字符串
        if (this.total <= 5) {
            for (let i = 1; i <= this.total; i++) {
                ul += `<li ${this.current === i ? 'class="current"' : ''}">${i}</li>`
            }
        }
        if (this.total > 5) {
            if (this.current === 1 || this.current === 2 || this.current === 3) {
                for (let i = 1; i < 6; i++) {
                    ul += `<li ${this.current === i ? 'class="current"' : ''}>${i}</li>`
                }
                ul += '<li>末页</li>'
                
            } else if (this.current === this.total || this.current === (this.total - 1) || this.current === (this.total - 2)) {
                 ul += '<li>首页</li>'
                 for (let i = this.total - 4; i <= this.total; i++) {
                    ul += `<li ${this.current === i ? 'class="current"' : ''}>${i}</li>`
                 }
            } else {
                ul += '<li>首页</li>'
                for (let i = this.current - 2; i <= this.current + 2; i++) {
                    ul += `<li ${this.current === i ? 'class="current"' : ''}>${i}</li>`
                }
                ul += '<li>末页</li>'
            }
        }
        
        return ul;
    }

    function val(current) {
        if (arguments.length === 0) return this.current;
        if (current < 1 || current > this.total || current === this.current) return;
        this.current = current;
        this.el.innerHTML = this.html();
    };
}
</script>
```
85. （移动控制）界面中存在id=jsContainer的节点A，系统会随机生成id为jsLayout的 m行 x n列 表格(m >= 1, n >= 1)，并随机选中一个td节点，请按照如下需求实现bind函数
1、bind 函数为document绑定keydown事件，当系统触发上(键值38)下(键值40)左(键值37)右(键值39)按键时，请找到当前选中的td节点，并根据当前指令切换高亮节点，具体效果参考以下图片  
2、在第一列往左移动则到达最后一列；在最后一列往右移动则到达第一列；在第一行往上移动则到达最后一行；在最后一行往下移动则到达第一行；  
3、请不要手动调用bind函数  
4、当前界面为系统在节点A中生成 9 * 9 表格并随机选中一个td节点后的效果  
5、请不要手动修改html和css，请不要修改js中的事件绑定方式  
6、不要使用第三方插件  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <title>Document</title>
</head>
<style>
table.game {
    font-size: 14px;
    border-collapse: collapse;
    width: 100%;
    table-layout: fixed;
}
table.game td {
    border: 1px solid #e1e1e1;
    padding: 0;
    height: 30px;
    text-align: center;
}
table.game td.current{
    background: #1890ff;
}
</style>
<body>
    <div id="jsContainer">
        <table class="game">
            <tbody>
                <tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
                <tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
                <tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
                <tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
                <tr><td></td><td></td><td></td><td></td><td class="current"></td><td></td><td></td><td></td><td></td></tr>
                <tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
                <tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
                <tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
                <tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
            </tbody>
        </table>
    </div>
</body>
</html>
<script>
function bind() {
    const jsContainer = document.querySelector('#jsContainer')
    const current = document.querySelector('.current')
    
    const m = document.querySelectorAll('tr')[0].childNodes.length
    const n = document.querySelectorAll('tr').length

    document.onkeydown = event => {
        if (!event) return;
        var code = event.keyCode || '';
        if (!{'37': 1, '38': 1, '39': 1, '40': 1}[code]) return;
        event.preventDefault && event.preventDefault();
        //TODO: 请实现按键控制
        
        if (m > 1 && n > 1) {
            let current = document.querySelector('.current')
            let x = 0
            let preElement = current
            while(preElement.previousElementSibling) {
                x++
                preElement = preElement.previousElementSibling
            }
            if (code === 37) { // 左
                if (current.previousElementSibling) {
                    current.previousElementSibling.className = 'current'
                } else {
                    current.parentElement.children[m - 1].className = 'current'
                }
            }
            if (code === 39) { // 右
                if (current.nextElementSibling) {
                    current.nextElementSibling.className = 'current'
                } else {
                    current.parentElement.children[0].className = 'current'
                }
            }
            if (code === 38) { // 上
                if (current.parentElement.previousElementSibling) {
                    current.parentElement.previousElementSibling.children[x].className = 'current'
                } else {
                    current.parentElement.parentElement.children[n - 1].children[x].className = 'current'
                }
            }
            if (code === 40) { // 下
                if (current.parentElement.nextElementSibling) {
                    current.parentElement.nextElementSibling.children[x].className = 'current'
                } else {
                    current.parentElement.parentElement.children[0].children[x].className = 'current'
                }
            }
            current.className = ''
        }
        
    };
}
bind()
</script>
```
86. （dom节点转成json数据）页面上存在id=jsContainer的节点A，系统会随机在节点A中生成文档片段，请按照如下需求实现 dom2json 函数  
1、dom2json需要分析整个节点A的dom结构，并将其结构转换为对应的json对象  
2、需要获取dom结构的标签名称(tag)，所有属性(attributes)，子节点(children)  
3、文档片段中的属性形式均为 name="value"，解析之后的格式为{name: value}, 属性值为String类型，不需要做解析  
4、随机生成的文档片段中，只包含 nodeType 为1(element)和3(text)的节点，不需要考虑其他节点类型  
5、纯文本也视为一个节点, json格式为 {tag: 'text', content: '文本内容'}，content为文本内容执行trim后的结果，如果该结果为空，则忽略当前节点  
6、返回结果中的标签名称不区分大小写  
7、如果节点不包含属性值或者子节点，其对应的结果中需要保留attributes以及children字段，例如 {tag: 'div', attributes: {}, children: []}  
8、当前界面执行dom2json之后的结果为如下图所示  
9、请不要手动修改html和css  
10、不要使用第三方插件  
```json
{
	"tag": "div",
	"attributes": {
		"id": "jsContainer"
	},
	"children": [{
		"tag": "ul",
		"attributes": {
			"class": "js-test",
			"id": "jsParent"
		},
		"children": [{
			"tag": "li",
			"attributes": {
				"data-index": "0"
			},
			"children": [{
				"tag": "text",
				"content": "1"
			}]
		}, {
			"tag": "li",
			"attributes": {
				"data-index": "1"
			},
			"children": [{
				"tag": "text",
				"content": "2"
			}]
		}]
	}, {
		"tag": "span",
		"attributes": {
			"style": "font-weight: bold;"
		},
		"children": [{
			"tag": "text",
			"content": "3"
		}]
	}, {
		"tag": "text",
		"content": "4"
	}]
}
```
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <div id="jsContainer">
        <ul class="js-test" id="jsParent">
            <li data-index="0">1</li>
            <li data-index="1">2</li>
        </ul>
        <span style="font-weight: bold;">3</span>
        4
    </div>
</body>
</html>
<script>
function dom2json() {
    const fn = (node) => {
        let obj = {
            tag: node.nodeName.toLowerCase(),
            attributes: [].reduce.call(node.attributes, (acc, cur) => {
                acc[cur.nodeName] = cur.value
                return acc
            }, {}),
            children: Array.from(node.childNodes).reduce((acc, cur) => {
                if (cur.nodeName === '#text') {
                    let content = cur.nodeValue.trim()
                    if (content) acc.push({
                        tag: 'text',
                        content
                    })
                } else acc.push(fn(cur))
                return acc
            }, [])
        }
        return obj
    }
    return fn(jsContainer)
}
</script>
```
87. （设置标签）本题展示了一个简化版的标签输入框，功能如下：  
1、当用户输入内容并敲回车键时，将输入框的内容在输入框前显示成标签，并清空输入框内容  
2、当用户敲删除键时，如果输入框当前没有内容，则删除前一个标签  
3、标签需要去掉字符串两端的多余的空格  
4、标签不能为空字符串  
5、标签不能重复，如果输入已存在的内容相同的标签，则不添加，并清空输入框  
6、请补充完成tagInput.init、tagInput.bindEvent、tagInput.addTag、tagInput.removeTag函数，实现上面的需求  
7、相关键码值，回车键=13，删除键=8  
8、请不要手动修改html和css  
9、不要使用第三方插件  
10、请使用ES5语法  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <title>Document</title>
</head>
<style>
.tag-input{
    position: relative;
    border: 1px solid #cccccc;
    padding: 0 5px;
    display: flex;
    flex-flow: row wrap;
}
.js-input{
    width: 450px;
    height: 22px;
    line-height: 22px;
    font-size: 16px;
    padding: 0;
    margin: 5px 0;
    outline: none;
    border: none;
    width: 6.5em;
    height: 24px;
    line-height: 24px;
}
.tag{
    padding: 0 10px;
    margin: 5px 5px 5px 0;
    background: #25bb9b;
    color: #ffffff;
    height: 24px;
    line-height: 24px;
    border-radius: 12px;
    font-size: 13px;
}
</style>
<body>
    <div class="tag-input">
        <span class="tag">前端</span>
        <span class="tag">编程题</span>
        <span class="tag">示例</span>
        <span class="tag">标签</span>
        <input type="text" class="js-input" maxlength="6" placeholder="请输入标签">
    </div>
</body>
</html>
<script>
var tagInput = {
    isInited: false,
    init: init,
    bindEvent: bindEvent,
    addTag: addTag,
    removeTag: removeTag
};
tagInput.init();

function init() {
    var that = this;
    if (that.isInited) return;
    that.isInited = true;
    // 请修改这一行代码，保存class为js-input的输入框的dom元素引用
    that.input = document.querySelector('.js-input');
    that.bindEvent();
}

function bindEvent() {
    var that = this;
    var input = that.input;
    if (!input) return;
    input.addEventListener('keydown', function (event) {
        // 请修改这一行代码，判断用户是否按了回车键
        var isEnter = event.keyCode === 13 ? true : false;
        // 请修改这一行代码，判断用户是否按了删除键
        var isDelete = event.keyCode === 8 ? true : false;

        (isEnter || isDelete) && event.preventDefault();
        isEnter && that.addTag();
        isDelete && that.removeTag();
    });
    input.parentNode.addEventListener('click', function () {
        input.focus();
    });
}

function addTag() {
    let that = this
    let input = that.input
    let value = input.value.trim()
    if (!value) return
    let tags = document.querySelectorAll('.tag')
    if (Array.from(tags).some(v => input.value === v.innerText)) {
        input.value = ''
        return 
    }
    let tagInput = document.querySelector('.tag-input')
    let span = document.createElement('span')
    span.className = 'tag'
    span.innerText = value
    tagInput.insertBefore(span, input)
    input.value = ''
}
function removeTag() {
    let that = this
    let input = that.input
    if (input.value) {
        input.value = input.value.slice(0, input.value.length - 1)
    } else {
        let tags = document.querySelectorAll('.tag')
        let tagInput = document.querySelector('.tag-input')
        if (tags.length) {
            tagInput.removeChild(tags[tags.length - 1])
        }
    }
}
</script>
```
88. （选择组件）CheckGroup是一个选择组件类，支持单选和多选  
选项参数格式：  
var options = [{text: '选项a', value: 'a'}, {text: '选项b', value: 'b'}, {text: '选项c', value: 'c'}, {text: '选项d', value: 'd'}];  
实例化单选组件：  
var item = new CheckGroup(document.getElementById('jsCheckGroup'), options);
item.val(['a']);  
实例化多选组件：  
var item = new CheckGroup(document.getElementById('jsCheckGroup'), options, true);
item.val(['a']);  
具体功能和需求如下：
1、单选组件请在 div.checkgroup 元素加上class radius  
2、选中时，请在对应选项dom元素加上class selected  
3、点击单选选项，如果未选中当前选项则选中当前选项并取消其他选项，否则取消当前选项  
4、点击多选选项，如果未选中当前选项则选中当前选项，否则取消当前选项  
5、给定的options中, text和value属性的值均为非空字符串  
6、val方法的参数和返回值均为数组(单选时数组长度不超过)  
7、请阅读代码，并根据注释完成对应代码(方法initHtml、toggleEl、isSelected、val)  
8、请不要手动修改html和css  
9、不要使用第三方插件  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <title>Document</title>
</head>
<style>
.checkgroup .item{
    height: 42px;
    line-height: 42px;
    padding: 0 10px;
    margin: 10px 0;
    border: 1px solid #c7c7c7;
    border-radius: 6px;
}
.checkgroup.radius .item{
    border-radius: 21px;
}
.checkgroup .item.selected{
    border: 1px solid #08b292;
    background: #08b292;
    color: #ffffff;
}
</style>
<body>
    <div id="jsCheckGroup">
    </div>
</body>
</html>
<script>
function CheckGroup(renderTo, options, isMultiple) {
	var that = this;
	that.renderTo = renderTo;
	that.options = options;
	that.isMultiple = !!isMultiple;
	that.initHtml();
	that.initEvent();
}
CheckGroup.prototype.initHtml = fInitHtml;
CheckGroup.prototype.initEvent = fInitEvent;
CheckGroup.prototype.toggleEl = fToggleEl;
CheckGroup.prototype.isSelected = fIsSelected;
CheckGroup.prototype.val = fVal;

function fInitHtml() {
	var that = this;
	// 请补全代码，拼接html字符串
	var sHtml = `<div class="checkgroup${that.isMultiple ? "" : " radius"}">`;
	for (let i = 0; i < that.options.length; i++) {
		sHtml += `<div data-val="${that.options[i].value}" class="item">${that.options[i].text}</div>`;
	}
	sHtml += "</div>";
	that.renderTo.innerHTML = sHtml;
	// 请补全代码，获取checkgroup的dom元素引用
	that.el = document.getElementsByClassName("checkgroup")[0];
}

function fInitEvent() {
	var that = this;
	that.el && that.el.addEventListener('click', function(event) {
		var item = event.target;
		item.classList.contains('item') && that.toggleEl(item);
	});
}

function fToggleEl(item) {
	// 根据当前是单选还是多选，以及当前元素是否选中，高亮/取消���亮指定的选项dom元素
	var that = this;
	if (that.isSelected(item)) {
		// 请补全代码
		item.classList.remove("selected");
	} else if (that.isMultiple) {
		// 请补全代码
		item.classList.add("selected");
	} else {
		// 请补全代码
		let itemList = document.getElementsByClassName("item");
		for (let i = 0, len = itemList.length; i < len; i++) {
			if (itemList[i].classList.contains("selected")) {
				itemList[i].classList.remove("selected");
				break;
			}
		}
		item.classList.add("selected");
	}
}

function fIsSelected(item) {
	// 请补全代码，判断item是否选中
	return item.classList.contains("selected");
}

function fVal(values) {
	var that = this;
	if (arguments.length === 0) {
		// 请补全代码，获取高亮的选项元素
		var items = document.getElementsByClassName("selected");
		// 请补全代码，获取高亮的选项元素的data-val
		var result = [];
		for(let i = 0; i<items.length; i++){
			let item = items[i];
			result.push(item.attributes["data-val"].value);
		}
		return result;
	}!that.isMultiple && values.length > 1 && (values.length = 1);
	// 请补全代码，获取所有的选项元素
	var items = document.getElementsByClassName("item");
	// 请补全代码，在指定元素上加上高亮的class
	for(let i = 0; i<items.length; i++){
		let item = items[i];
		if (values.includes(item.attributes["data-val"].value)) {
			item.classList.add("selected")
		} else {
			item.className = 'item';
		}
	}
}
var options = [{text: '选项a', value: 'a'}, {text: '选项b', value: 'b'}, {text: '选项c', value: 'c'}, {text: '选项d', value: 'd'}];

var item = new CheckGroup(document.getElementById('jsCheckGroup'), options);
</script>
```
89. 
本题展示了一个简化版的计算器，需求如下：  
1、除法操作时，如果被除数为0，则结果为0  
2、结果如果为小数，最多保留小数点后两位，如 2 / 3 = 0.67(显示0.67), 1 / 2 = 0.5(显示0.5)  
3、请阅读并根据提示补充完成函数initEvent、result和calculate  
4、请不要手动修改html和css  
5、不要使用第三方插件  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <title>Document</title>
</head>
<style>
body, ul, li,select {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
ul,li {list-style: none;}
.calculator {
    max-width: 300px;
    margin: 20px auto;
    border: 1px solid #eee;
    border-radius: 3px;
}
.cal-header {
    font-size: 16px;
    color: #333;
    font-weight: bold;
    height: 48px;
    line-height: 48px;
    border-bottom: 1px solid #eee;
    text-align: center;
}
.cal-main {
    font-size: 14px;
}
.cal-main .origin-value {
    padding: 15px;
    height: 40px;
    line-height: 40px;
    font-size: 20px;
    text-align: right;
    overflow: hidden;
    text-overflow:ellipsis;
    white-space: nowrap;
}
.cal-main .origin-type,
.cal-main .target-type {
    padding-left: 5px;
    width: 70px;
    font-size: 14px;
    height: 30px;
    border: 1px solid #eee;
    background-color: #fff;
    vertical-align: middle;
    margin-right: 10px;
    border-radius: 3px;
}
.cal-keyboard {
    overflow: hidden;
}
.cal-items {
    overflow: hidden;
}
.cal-items li {
    user-select: none;
    float: left;
    display: inline-block;
    width: 75px;
    height: 75px;
    text-align: center;
    line-height: 75px;
    border-top: 1px solid #eee;
    border-left: 1px solid #eee;
    box-sizing: border-box;
}
li:nth-of-type(4n+1) {
    border-left: none;
}
li[data-action=operator] {
    background: #f5923e;
    color: #fff;
}
.buttons {
    float: left;
    width: 75px;
}
.buttons .btn {
    width: 75px;
    background-color: #fff;
    border-top: 1px solid #eee;
    border-left: 1px solid #eee;
    height: 150px;
    line-height: 150px;
    text-align: center;
}
.btn-esc {
    color: #ff5a34;
}
.btn-backspace {
    position: relative;
}
</style>
<body>
    <div class="calculator">
        <header class="cal-header">简易计算器</header>
        <main class="cal-main">
            <div class="origin-value">0</div>
            <div class="cal-keyboard">
                <ul class="cal-items">
                    <li data-action="num">7</li>
                    <li data-action="num">8</li>
                    <li data-action="num">9</li>
                    <li data-action="operator">÷</li>
                    <li data-action="num">4</li>
                    <li data-action="num">5</li>
                    <li data-action="num">6</li>
                    <li data-action="operator">x</li>
                    <li data-action="num">1</li>
                    <li data-action="num">2</li>
                    <li data-action="num">3</li>
                    <li data-action="operator">-</li>
                    <li data-action="num">0</li>
                    <li data-action="operator">清空</li>
                    <li data-action="operator">=</li>
                    <li data-action="operator">+</li>
                </ul>
            </div>
        </main>
    </div>
</body>
</html>
<script>
var Calculator = {
  init: function () {
    var that = this;
    if (!that.isInited) {
      that.isInited = true;
      // 保存操作信息
      // total: Number, 总的结果
      // next: String, 下一个和 total 进行运算的数据
      // action: String, 操作符号
      that.data = {total: 0, next: '', action: ''};
      that.bindEvent();
    }
  },
  bindEvent: function () {
    var that = this;
    // 请补充代码：获取 .cal-keyboard 元素
    var keyboardEl = document.querySelector(".cal-keyboard");
    keyboardEl && keyboardEl.addEventListener('click', function (event) {
      // 请补充代码：获取当前点击的dom元素
      var target = event.path[0];
      // 请补充代码：获取target的 data-action 值
      var action = target.dataset.action;
      // 请补充代码：获取target的内容
      var value = target.innerText;
      if (action === 'num' || action === 'operator') {
        that.result(value, action === 'num');
      }
    });
  },
  result: function (action, isNum) {
    var that = this;
    var data = that.data;
    if (isNum) {
      data.next = data.next === '0' ? action : (data.next + action);
      !data.action && (data.total = 0);
    } else if (action === '清空') {
      // 请补充代码：设置清空时的对应状态
      data.total = 0;
      data.next = "";
      data.action = "";
    } else if (action === '=') {
      if (data.next || data.action) {
        data.total = that.calculate(data.total, data.next, data.action);
        data.next = '';
        data.action = '';
      }
    } else if (!data.next) {
      data.action = action;
    } else if (data.action) {
      data.total = that.calculate(data.total, data.next, data.action);
      data.next = '';
      data.action = action;
    } else {
      data.total = +data.next || 0;
      data.next = '';
      data.action = action;
    }

    // ���补充代码：获取 .origin-value 元素
    var valEl = document.querySelector(".origin-value");
    valEl && (valEl.innerHTML = data.next || data.total || '0');
  },
  calculate: function (n1, n2, operator) {
    n1 = +n1 || 0;
    n2 = +n2 || 0;
    if (operator === '÷') {
      // 请补充代码：获取除法的结果
      // 【需求】1、除法操作时，如果被除数为0，则结果为0
      if(n2 === 0) return 0;
      n1 /= n2;
      // 【需求】2、结果如果为小数，最多保留小数点后两位，如 2 / 3 = 0.67(显示0.67), 1 / 2 = 0.5(显示0.5)
      if(String(n1).split(".")[1] && String(n1).split(".")[1].length > 2){
        n1 = n1.toFixed(2);
      }
      return n1 * 1;
    } else if (operator === 'x') {
      // 请补充代码：获取乘法的结果
      return n1 * n2;
    } else if (operator === '+') {
      // 请补充代码：获取加法的结果
      return Number((n1 + n2).toFixed(2));
    } else if (operator === '-') {
      // 请补充代码：获取减法的结果
      return Number((n1 - n2).toFixed(2));
    }
  }
};
Calculator.init();
</script>
```