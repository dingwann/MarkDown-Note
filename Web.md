# ***CSS***

## 1.基本操作

### 1.1 文字竖直方向排列+英文

![image-20240324162428642](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272004289.png)



## 2.布局操作

### 2.1 flex

以下作为举例：

```html
<body>
    <div class="flex-container">
        <div class="flex-item">
            <h1>CSS:层叠样式表</h1>
            <p>
                电影《沙丘》为观众呈现了一段神秘而感人至深的英雄之旅。天赋异禀的少年保罗·厄崔迪被命运指引，为了保卫自己的家族和人民，决心前往浩瀚宇宙间最危险的星球，开启一场惊心动魄的冒险。与此同时，各路势力为了抢夺这颗星球上一种能够释放人类最大潜力的珍贵资源而纷纷加入战场。最终，唯有那些能够战胜内心恐惧的人才能生存下去。
            </p>
        </div>
        <div class="flex-item">
            <h1>CSS:层叠样式表</h1>
            <p>
                电影《沙丘》为观众呈现了一段神秘而感人至深的英雄之旅。天赋异禀的少年保罗·厄崔迪被命运指引，为了保卫自己的家族和人民，决心前往浩瀚宇宙间最危险的星球，开启一场惊心动魄的冒险。与此同时，各路势力为了抢夺这颗星球上一种能够释放人类最大潜力的珍贵资源而纷纷加入战场。最终，唯有那些能够战胜内心恐惧的人才能生存下去。
            </p>
        </div>
        <div class="flex-item">
            <h1>CSS:层叠样式表</h1>
            <p>
                电影《沙丘》为观众呈现了一段神秘而感人至深的英雄之旅。天赋异禀的少年保罗·厄崔迪被命运指引，为了保卫自己的家族和人民，决心前往浩瀚宇宙间最危险的星球，开启一场惊心动魄的冒险。与此同时，各路势力为了抢夺这颗星球上一种能够释放人类最大潜力的珍贵资源而纷纷加入战场。最终，唯有那些能够战胜内心恐惧的人才能生存下去。
            </p>
        </div>
    </div>
</body>
```



#### 2.1.1 竖直方向居中

```css
* {
    margin: 0;
    padding: 0;
}

.flex-container {
    width: 100%;
    min-width: 500px;
    max-width: 800px;
    margin: 0 auto;
    background-color: pink;
    display: flex;
    align-items: center; /* 默认在顶部：flex-start(y轴正方向起点) */
}

.flex-item {
    padding: 10px;
    border: 1px solid gray;
    border-radius: 16px;
    background-color: yellowgreen;
}
```



#### 2.1.2 水平方向居中

```css
.flex-container {
    width: 100%;
    min-width: 500px;
    max-width: 800px;
    margin: 0 auto;
    background-color: pink;
    display: flex;
	justify-content: center; /* 默认在左侧：flex-start(x轴正方向起点) */
}

.flex-item {
    padding: 10px;
    border: 1px solid gray;
    border-radius: 16px;
    background-color: yellowgreen;
    max-width: 200px;
}
```



#### 2.1.3 非均分布局

```css
.flex-container {
    width: 100%;
    min-width: 500px;
    max-width: 800px;
    margin: 0 auto;
    background-color: pink;
    display: flex;
	
}

.flex-item {
    padding: 10px;
    border: 1px solid gray;
    border-radius: 16px;
    background-color: yellowgreen;
    flex: 1; /* 此时三个元素比例为1：1：1 */
}
```

```css
.flex-item {
    padding: 10px;
    border: 1px solid gray;
    border-radius: 16px;
    background-color: yellowgreen;
    flex: 1; /* 此时三个元素比例为1：1：1 */
}

.flex-item:nth-child(2) {
    flex: 2;
}
/* 此时三个元素比例为1：2：1 */
```

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272004176.png" alt="image-20240324200318360" style="zoom:50%;" />



### 2.2 grid(网格)

**二维，需要指定行和列**

```html
<body>
    <div class="grid-container">
        <div class="grid-item">
            <h1>1、CSS:层叠样式表</h1>
            <p>
                电影《沙丘》为观众呈现了一段神秘而感人至深的英雄之旅。天赋异禀的少年保罗·厄崔迪被命运指引，为了保卫自己的家族和人民，决心前往浩瀚宇宙间最危险的星球，开启一场惊心动魄的冒险。与此同时，各路势力为了抢夺这颗星球上一种能够释放人类最大潜力的珍贵资源而纷纷加入战场。最终，唯有那些能够战胜内心恐惧的人才能生存下去。
            </p>
        </div>
        <div class="grid-item">
            <h1>2、CSS:层叠样式表</h1>
            <p>
                电影《沙丘》为观众呈现了一段神秘而感人至深的英雄之旅。天赋异禀的少年保罗·厄崔迪被命运指引，为了保卫自己的家族和人民，决心前往浩瀚宇宙间最危险的星球，开启一场惊心动魄的冒险。与此同时，各路势力为了抢夺这颗星球上一种能够释放人类最大潜力的珍贵资源而纷纷加入战场。最终，唯有那些能够战胜内心恐惧的人才能生存下去。
            </p>
        </div>
        <div class="grid-item">
            <h1>3、CSS:层叠样式表</h1>
            <p>
                电影《沙丘》为观众呈现了一段神秘而感人至深的英雄之旅。天赋异禀的少年保罗·厄崔迪被命运指引，为了保卫自己的家族和人民，决心前往浩瀚宇宙间最危险的星球，开启一场惊心动魄的冒险。与此同时，各路势力为了抢夺这颗星球上一种能够释放人类最大潜力的珍贵资源而纷纷加入战场。最终，唯有那些能够战胜内心恐惧的人才能生存下去。
            </p>
        </div>
        <div class="grid-item">
            <h1>4、CSS:层叠样式表</h1>
            <p>
                电影《沙丘》为观众呈现了一段神秘而感人至深的英雄之旅。天赋异禀的少年保罗·厄崔迪被命运指引，为了保卫自己的家族和人民，决心前往浩瀚宇宙间最危险的星球，开启一场惊心动魄的冒险。与此同时，各路势力为了抢夺这颗星球上一种能够释放人类最大潜力的珍贵资源而纷纷加入战场。最终，唯有那些能够战胜内心恐惧的人才能生存下去。
            </p>
        </div>
        <div class="grid-item">
            <h1>5、CSS:层叠样式表</h1>
            <p>
                电影《沙丘》为观众呈现了一段神秘而感人至深的英雄之旅。天赋异禀的少年保罗·厄崔迪被命运指引，为了保卫自己的家族和人民，决心前往浩瀚宇宙间最危险的星球，开启一场惊心动魄的冒险。与此同时，各路势力为了抢夺这颗星球上一种能够释放人类最大潜力的珍贵资源而纷纷加入战场。最终，唯有那些能够战胜内心恐惧的人才能生存下去。
            </p>
        </div>
        <div class="grid-item">
            <h1>6、CSS:层叠样式表</h1>
            <p>
                电影《沙丘》为观众呈现了一段神秘而感人至深的英雄之旅。天赋异禀的少年保罗·厄崔迪被命运指引，为了保卫自己的家族和人民，决心前往浩瀚宇宙间最危险的星球，开启一场惊心动魄的冒险。与此同时，各路势力为了抢夺这颗星球上一种能够释放人类最大潜力的珍贵资源而纷纷加入战场。最终，唯有那些能够战胜内心恐惧的人才能生存下去。
            </p>
        </div>
    </div>
</body>
```

```css
.grid-container {
    display: grid;
    grid-template-columns: 200px 100px 200px; /* 规定3列，剩下的元素自动往下排列 */
    /*
    grid-template-columns: 20% 50% 30%; 百分比显示
    grid-template-columns: 1fr 1fr 1fr; 比例：1 ：1：1 自适应尺寸
    grid-template-columns: repeat(3, 1fr); 重复写三个1fr
    grid-template-columns: repeat(auto-fill, 200px); 自动尽可能填充，元素200px宽，随着窗口大小改变而适配
    grid-template-columns: 300px auto 300px; 3列，左右两侧300px固定，中间自适应。 
    */
}
```

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272004420.png" alt="image-20240324201417080" style="zoom:50%;" />



**高度**

```css
.grid-container {
    display: grid;
    grid-template-columns: 300px auto 300px;
    height: 600px;
    grid-template-rows: 1fr 2fr;
}

.grid-item {
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 16px;
    background-color: pink;
    overflow: hidden;
}
```

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272004541.png" alt="image-20240324202713715" style="zoom:50%;" />



## 3.过渡、变换、动画

### 3.1 过渡(transition)

```css
.a-box {
    width:100px;
	transition:width 1s (运动方式)
}

.a-box：hover{
	width：200px;
}
```

高度、背景同理

```css
.a-box {
    width:100px;
    height:100px;
	transition:width 1s, height 2s;
    /* transition:all 300ms; */
    /* transition:300ms; */
}

.a-box:hover {
	width：200px;
    height:200px;
}
```

运动方式：linear（匀速）、默认easy。easy-in 、easy-in-out

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272004374.png" alt="image-20240324171012047" style="zoom: 50%;" />



### 3.2 变换(transform)

#### 3.2.1 元素位置上的变化

```css
.b-box {
    width:200px;
    height:200px;
    background-color:pink;
    transition: all 300ms;
}
```

```css
.b-box:hover {
    /* transform: translate(100px,20px); */
    transform: translateX(100px) translateY(20px);
}
```



#### 3.2.2 角度旋转

```css
.b-box {
    width:200px;
    height:200px;
    background-color:pink;
    transition: all 300ms;
    transform-origin: center;/* 旋转中心，默认就是中心，要放在元素上。右下：right bottom */
}
```

```css
.b-box:hover {
    transform: rotate(30deg);
}
```



#### 3.2.3 缩放

```css
.b-box {
    width:200px;
    height:200px;
    background-color:pink;
    transition: all 300ms;
    transform-origin: center;/* 旋转中心，默认就是中心，要放在元素上。右下：right bottom*/
}
```

```css
.b-box:hover {
    transform:scale(.5, 2); /* .5:水平方向缩小0.5  2:竖直方向放大2倍 */
}
```



#### 3.2.4 扭曲倾斜

```css
.b-box {
    width:200px;
    height:200px;
    background-color:pink;
    transition: all 300ms;
    transform-origin: center;/* 旋转中心，默认就是中心，要放在元素上。右下：right bottom*/
}
```

```css
.b-box:hover {
    transform:skew(-20deg); /* x轴正方向倾斜 */
}
```



#### 3.2.5 3D变换

需要指定容器说明进行3D渲染

以class='container'的div举例，需要3d渲染的元素全放在其下，这里包含class='a'的div示例。

```css
.container {
    width: 200px;
    margin: 0 auto;
    transform-style: preserve-3d;
    perspective: 500px;
}
```

```css
.a {
    width: 200px;
    height: 200px;
    background-color: pink;
    transition: 300ms;
}
```

```css
.a:hover {
    transform: translate3d(x,y,z); /* 三个轴 */
    transform: rotate3d(x, y, z, 100deg);
}
```

------

**2d与3d的立体变换**

```html
<div class="container">
    <div class="a"></div>
    <div class="b"></div>
</div>
```

```css
* {
    margin: 0;
    padding: 0;
}

.container {
    width: 200px;
    transform-style: preserve-3d;
    perspective: 500px;
    position: relative;
    margin: 0 auto;
    transition: 3s;
}

.container:hover {
    transform: rotate3d(0, 1, 0, 180deg);
}

.a {
    width: 200px;
    height: 200px;
    background-color: pink;
    position: absolute;
    transition: 1s;
}

.b {
    width: 200px;
    height: 200px;
    background-color: yellowgreen;
    position: absolute;
    transition: 1s;
    transform: translateZ(-100px);
}
```



### 3.3 动画

关键帧

```css
@keyframes changecolor{
    0% {
        background-color: aliceblue;
    }

    50% {
        background-color: antiquewhite;
    }

    100% {
        background-color: aliceblue;
    }
}
```

```css
.b {
    width: 200px;
    height: 200px;
    background-color: pink;
    position: absolute;
    transition: 1s;
    animation: changecolor 2s infinite; /* infinite无限循环 */
}
```

# ***JS***

## 1.BOM与DOM

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <div id="wc">Wangcai</div>
    <script type="module">
        const obj = document.getElementById('wc')
        obj.textContent = 'Liuwang'
        console.log(obj)
    </script>
</body>
</html>
```

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272004220.png" alt="image-20240324213440807" style="zoom: 67%;" />

**document.getElementsByTagName()   // 标签选择**



```html
// 通用选择器
document.querySelectorAll('')  选择器选择所有匹配的
document.querySelector('')     选择器选择第一个匹配的
```



### 1.1 同级相邻元素的获取

```html
<body>
    <div id="wc">
        Wangcai
        <p>1</p>
        <p class="a">2</p>
        <p>3</p>
        <p>4</p>
    </div>
    <script type="module">
        const obj = document.getElementById('wc')
        const ll = document.querySelector('#wc .a')
        ll.previousElementSibling.textContent = '111'  // 选择同级前一个元素并设置文本
        ll.nextElementSibling      // 选择同级后一个元素
    </script>
</body>
```



### 1.2 **父元素的获取**

```html
<body>
    <div id="wc">
        Wangcai
        <p>1</p>
        <p class="a">2</p>
        <p>3</p>
        <p>4</p>
    </div>
    <script type="module">
        const ll = document.querySelector('.a')
        const wc = ll.parentNode
        console.log(wc)
    </script>
</body>
```

![image-20240324215253421](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272003377.png)





### 1.3 基于父元素获取子元素

```html
<body>
    <div id="wc">
        Wangcai
        <p>1</p>
        <p class="a">2</p>
        <p>3</p>
        <p>4</p>
    </div>
    <script type="module">
        const ll = document.querySelector('.a')
        const wc = ll.parentNode
        const item = wc.children
        console.log(item)
    </script>
</body>
```

![image-20240324215637769](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272003710.png)



### 1.4 样式处理

```html
    <style>
        * {
            padding: 0;
            margin: 0;
        }

        div {
            width: 200px;
            height: 200px;
            border: 1px dashed #ccc;
            margin-bottom: 10px;
            background-color: pink;
        }
    </style>
</head>
<body>
    <div id="block"></div>
    <script type="module">
        const block = document.querySelector('#block')
        // block.style.width = '300px'
        // block.style.height = '100px'
    </script>
</body>
```

![image-20240324220631878](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272003499.png)

***注释取消***

![image-20240324220704537](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272003249.png)

***优化方法,提前预设***

```html
<style>
	.changeStyle {
	width: 80px;
	height: 80px;
	background-color: tomato;
}
</style>

<body>
    <div id="block"></div>
    <script type="module">
        const block = document.querySelector('#block')
        // block.style.width = '300px'
        // block.style.height = '100px'
        block.className = 'changeStyle'
    </script>
</body>
```

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272003626.png" alt="image-20240324221302365" style="zoom: 25%;" />



<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272003334.png" alt="image-20240324221325527" style="zoom:50%;" />



### 1.5 文本处理

**text.Content只能纯文本**

**innerHTML可以进行标签生成**

```html
<body>
    <div id="block"></div>
    <script type="module">
        const block = document.querySelector('#block')
		block.innerHTML = 'wangcai<span>HaHaHa!</span>'
    </script>
</body>
```

![image-20240324221848962](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272003015.png)



### 1.6 事件处理

**交互方式**

![image-20240324222203266](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272003278.png)



存在覆盖问题：

```html
<body>
    <div id="block"></div>
    <script type="module">
        const block = document.querySelector('#block')
		block.onclick = function() {
            alert("Hello,World!")  // 弹窗
        }
    </script>
</body>
```

解决：

```html
<body>
    <div id="block"></div>
    <script type="module">
        const block = document.querySelector('#block')
        block.addEventListener('click', function() {
            alert('Wangcai')
        })
        block.addEventListener('click', function() {
            alert('Wangcai Again')
        })
    </script>
</body>
```

**轮播图JS的实现**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .test {
            width: 100px;
            height: 100px;
            position: relative;
            padding-left: 0;
        }
        .test li {
            position: absolute;
            width: 100px;
            height: 100px;
            line-height: 100px;
            text-align: center;
            text-shadow: 0 0 5px #000;
            font-size: 30px;
            color: #fff;
            opacity: 0;
            transition: opacity 1s;
            list-style-type:none
        }

        .test li:nth-child(1) {
            background-color: rebeccapurple;
        }
        .test li:nth-child(2) {
            background-color: yellowgreen;
        }
        .test li:nth-child(3) {
            background-color: tomato;
        }
        .test li:nth-child(4) {
            background-color: blanchedalmond;
        }

        .test li.active {
            opacity: 1;
        }
    </style>
</head>
<body>
    <div id="container">
        <ul class="test">
            <li class="active">11111</li>
            <li>22222</li>
            <li>33333</li>
            <li>44444</li>
        </ul>
        <button id="prev">上一张</button>
        <button id="next">下一张</button>
    </div>
    <script type="module">
        const ul = document.querySelector('.test')
        const items = ul.children
        const prev = document.querySelector('#prev')
        const next = document.querySelector('#next')
        let index = 0;
        next.addEventListener('click',function() {
            console.log(index)
            if(index !== -1) {
                items[index].className = ''
            }
            if(index === items.length - 1) {
                index = -1; 
            }
            index ++;
            items[index].className='active'
        })
        prev.addEventListener('click',function() {
            items[index].className = ''
            if(index === 0) {
                index = items.length
            }
            index --
            items[index].className='active'
        })    
    </script>
</body>
</html>
```

![image-20240324235248537](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272003730.png)

### 1.7 定时器

**setTimeout：**xx秒后执行一次

```js
setTimeout(function(){
    alert('Hello')
},2000)  // 2s
```

**setInterval：**间隔xx秒执行一次

```js
setInterval(function(){
    console.log('Hello')
},2000)   // 每2s执行一次
```

**setInterval会返回一个唯一的ID标识**

停止：

```js
const timer = setInterval(function(){
    console.log('Hello')
},2000)

setTimeout(function(){
    clearInterval(timer)
},6000)
```

# *ES6 标准*

## 1. 变量和常量

**let声明变量     const声明常量**

**{} ----> 规定作用域，可在其内书写代码**

```js
{
	let count = 0;
	count ++;
    
    const BASE_URL= 'http://www.baidu.com'  // 常量一般规范为大写命令
    BASE_URL= 3;   // 报错，因为常量不可修改
}

console.log(count);  // 此时报错count未定义
```



## 2. 模板字符串

```js
const str1 = 'abc'
const str2 = `${str1}efg`
const str3 = `
可进行多行书写和读取变量
${str2}
`
console.log(str2,str3)
```



## 3. 解构赋值

```js
const [a, b, c] = [1, 2, 3]  // a = 1, b = 2, c = 3
console.log(a, b, c)
```

```js
const obj = {
    name: 'wangcai',
    age: 18,
    email: 'xxxx@163.com',
    addr: '四川省成都市xxx区'
}

const {name, age:userAge, ...wc} = obj   // age: userAge改名操作  ...wc 接收剩余值
// 将const obj中的 obj 改成 {name, age:userAge, ...wc} 等效
console.log(name, userAge, wc)
```

![image-20240325150902037](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272003423.png)



## 4. 数组和对象的扩展

### 4.1 扩展运算符的使用

```js
const arr = [11, 22, 33]
const res = [...arr, 44, 55]    // ...xxx 用于解包
console.log(res)
```

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272004716.png" alt="image-20240325150703064" style="zoom: 80%;" />

```js
const obj1 = {
    a: 1
}
const obj2 = {
    b: 2
}
const obj3 = {
    name: 'wangcai',
    ...obj1,
    ...obj2
}
console.log(obj3)
```

![image-20240325151704456](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272003301.png)

### 4.2 数组方法

```js
// arguments是函数中用于接收所有形参的
function fn() {
    console.log(arguments)
}
fn(1, 2, 3, 4)
```

![image-20240325152205874](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272003807.png)

```js
// 此时的arguments具有数组的形式，但是没有数组的功能，称为伪数组，如下使用push会报错
function fn() {
    arguments.push(5)
    console.log(arguments)
}
fn(1, 2, 3, 4)
```

![image-20240325152327243](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272003840.png)



**伪数组转换为数组**

```js
// Array.from()
function fn() {
    Array.from(arguments).forEach(items => {
        console.log(items)
    })
}
fn(1, 2, 3, 4)
```

![image-20240325152635401](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272003754.png)



### 4.3 对象的方法

****

**Object.assign()**  **拷贝/合并    接收多个参数，后面的参数会合并**  

```js
const objA = {
    name: 'wangcai',
    age: 18
}

const objB = Object.assign({}, objA)
objB.name = 'wc'
console.log(objA, objB)
```

![image-20240325183317186](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272003990.png)

```js
const objA = {
    name: 'wangcai',
    age: 18
}

const objB = {
	email: 'xxx@163.com'
}

const objC = Object.assign({}, objA, objB)

console.log(objC)
```

![image-20240325183532886](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272003493.png)



### 4.4 Class

```js
class A {
    constructor(name, age) {  // 构造函数  继承类函数 super() 写在这
        this.name = name
        this.age = age
    }
}

const c = new A('wangcai', 18)
console.log(c)
```

![image-20240325184229587](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272003355.png)

```js
class A {
    constructor(name, age) {
        this.name = name
        this.age = age
    }
}
//  继承类A并写一个方法
class B extends A {
    constructor(name, age, email) {
        super(name, age)  // 继承形参写过来 相当于调用父类的构造函数constructor
        this.email = email
    }

    introduce() {
        console.log(`Myname:${this.name},EmailAddr:${this.email}`)
    }
}

const b = new B('wc', 18, 'xxx@163.com')
b.introduce()
```

![image-20240325185433007](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272003254.png)



### 4.5 箭头函数（匿名函数）

```js
// 当参数为1，且表达式只有一行能解决时不需要大括号和return
const sum1 = n => n + 3;
console.log(sum1(10))

const sum2 = (n1, n2) => n1 + n2;
console.log(sum2(10, 10))

const sum3 = (n1, n2, ...other) => console.log(n1, n2, ...other);
console.log(sum3(10, 20, 30, 40, 50))

const sum4 = arr => {
    let sum = 0;
    arr.forEach(items => sum += items);
    return sum;
}
console.log(sum4([1, 2, 3, 4, 5]))
```

![image-20240327200226432](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272002563.png)



## 5. 异步处理

### 5.1 Promise

**异步任务在当前的同步任务执行完成后再进行**

Promise有两个参数：**resolve    reject**

```js
const p = new Promise((resolve, reject) => {
    resolve('任务成功的数据')
})
p.then(data => {
    console.log(data)
})
//resolve时p会得到状态并自动执行then方法传入回调函数
//reject时then就不会调用
```

![image-20240327202914483](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272029553.png)

```js
const p = new Promise((resolve, reject) => {
    reject('任务失败的信息')
})
p.then(data => {
    console.log(data)
})
.catch(err => {
    console.log(err)
})
```

![image-20240327203221389](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272032442.png)

```js
const p = new Promise((resolve, reject) => {
    resolve('任务1成功的信息')
})
p.then(data => {
    console.log("成功")
    return new Promise((resolve, reject) => {
        resolve('任务2成功的信息')
    })
})
.then  // 这里的then是对上一个返回的promise实例结果，每个then都是这样。
.catch(err => {
    console.log(err)
})

// then()包含了两个参数，第一个参数是上一级实例状态成功时执行的，第二个参数是失败时执行的。如果我们希望对于每上一个promise实例的失败处理都有对应方案时，我们应在该实例的then方法中书写第二个函数等价于catch，如果不书写将会找到后面第一个catch方法。
```

```js
/* 

then()返回一个新的Promise实例，这个新的Promise实例可以由用户自定义返回或系统自动返回。且只要 then() { return XXX } 中return返回的不是Promise，这个返回值就会被系统自动包装为一个 fulfilled 状态的Promise实例。

总之记住一句话：后面的then方法始终是对前面返回的Promise实例的处理，且前面返回的必须是Promise实例，若不是则会被系统自动帮我们返回，而且返回的是成功的promise对象，仅此而已。

*/
```

举例：

```js
const p = new Promise((resolve, reject) => {
    resolve('任务1的数据')   // reject('任务1的数据')
})
p.then(data => {
    console.log('任务1成功')
}, err => {
    return new Promise((resolve, reject) => {
        reject(console.log('任务1失败'))
    })
})
.then(data => {
    console.log('任务2成功')
}, err => {
    return new Promise((resolve, reject) => {
        reject(console.log('任务2失败'))
    })
})
.catch(err => {
    console.log('hh')
})
```

![image-20240327205913662](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272059745.png)



![image-20240327205954488](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272059545.png)

### 5.2 Async await

**基于Promise的简化功能语法糖，追求和同步写法完全一致的方式，但无法完全代替。**

async 用于申明一个 function 是异步的，而 await 用于等待一个异步方法执行完成。

async 函数返回的是一个 Promise 对象。

因为 async 函数返回一个 Promise 对象，所以 await 可以用于等待一个 async 函数的返回值——这也可以说是 await 在等 async 函数，但要清楚，它等的实际是一个返回值。注意到 await 不仅仅用于等 Promise 对象，它可以等任意表达式的结果，所以，await 后面实际是可以接普通函数调用或者直接量的。

```js
function asyncTask() {
    // ...
    return new Promise((resolve, reject) => {
        flag = true;
        if(flag) {
            resolve('任务2成功')
        }else{
            reject('任务2失败')
        }
    })
}
// 使用await的函数添加async
async function main() {
    console.log("1");
    const data = await asyncTask();
    console.log(data);
    console.log("3")
}
main()
// 达到同步任务的效果
```

![image-20240327212924185](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272129259.png)

### 5.3 Proxy 代理对象

目的：进行某个操作时能自动进行另一个操作，vue的响应式底层原理

```js
// body中有<div id='container'></div>
const obj = {name: 'wangcai', age: 18}
const container = document.getElementById('container')
const p = new Proxy(obj, {
    get(target, property) {  // 访问时操作
        return obj[property]
    },
    set(target, property, value) {  // 设置时操作
        obj[property] = value;
        container.textCont = obj.name
    }
})

p.name = 'wc'
```

操作方法：

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403272141118.png" alt="image-20240327214135037" style="zoom:50%;" />

### 5.4 Module 模块

**ESM**

代码的导出、导入，已学，略。

**CommonJS(node.js)**

```js
// a.js
module.exports = {
    a: 1,
    b: 2,
    c: 3
}
// 等价形式 module.export == module.exports
exports.a = 1
exports.b = 2
```

```js
// index.js type = 'module'
const moduleA = require('./a.js')
console.log(moduleA)
```

# *Node.js*

**NodeJS是脱离浏览器运行JS代码的环境。**

node -v  查看node版本

npm -v  查看npm版本

```js
console.log('Hello,World!')
```

![image-20240329135831781](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403291358902.png)

## 模块

Nodejs提供了模块系统让js文件可以互相调用，模块加载采用的是同步加载的commonjs规范。

**commonjs：**

每个文件都是一个封闭的模块，模块里定义的变量、函数、类都是私有的

module代表当前模块，module是封闭的，但它的exports属性向外提供调用接口

require加载模块，读取并执行一个js文件，然后返回该模块的exports对象

commonjs是同步加载的，因此模块加载的顺序严格按照书写顺序执行

模块可以多次加载，但在第一次加载后模块会被编译执行，放入缓存，后续的require之间从缓存中读取，模块代码不再编译

```js
// a.js
a = 10;
module.exports = a;
```

```js
// data.js
a = 'Wangcai';
module.exports = a;
```

```js
// index.js
const a = require('./a.js')
const data = require('./data.js')
console.log(a)
console.log(data)
```

![image-20240329142053703](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403291420816.png)

**模块化导出方式:**

global.xxx = 'xxx'  // 导出全局变量，只要导入相应js文件即可使用。

```js
// a.js
a = 10;
global.addr = 'x'
module.exports = a;
```

```js
// index.js
const a = require('./a.js')
const data = require('./data.js')
console.log(a)
console.log(data)
console.log(addr)
```

![image-20240329142938964](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403291429032.png)

![image-20240329143151957](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403291431041.png)

## HTTP

![image-20240417133037871](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202404171330126.png)

### 1. http.server

使用HTTP服务器和客户端，须使用require('http')

```js
const http = require('http');
const port = 3000;

const server = http.createServer((req,res) => {
    res.statusCode = 200;
    res.setHeader('Content-Type','text/plain;charset=utf-8');
    res.end('Wangcai');
})

server.listen(3000,() => {
    console.log('Start');
})
```

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403291448374.png" alt="image-20240329144816277" style="zoom: 150%;" />

![image-20240329144848636](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403291448681.png)

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403291452640.png" alt="image-20240329145217584" style="zoom:67%;" />



### 2. request响应体

```js
write
	向客户端返回数据，该方法可以调用多次，返回数据将拼接在一起
end
	结束请求，同时response.end方法也可以用来向前端返回数据
setHeader
	设置响应头，如果该头信息已经存在，则覆盖
statusCode
	设置响应状态
statusMessage
	设置响应状态信息
```

```js
const http = require('http');
const port = 3000;

const server = http.createServer((req,res) => {
    res.statusCode = 200;
    res.setHeader('Content-Type','text/plain;charset=utf-8');
    res.write('Hello')
    res.write('World')
    res.end('Wangcai');
})

server.listen(3000,() => {
    console.log('Start');
})
```

![image-20240329150239670](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403291502721.png)



### 3. 请求方式

**request**    or    **get**

两种请求都接受以下参数：

​	**url**：请求地址

​	**options**：请求配置

​	**callback**：请求成功回调

其中**options**配置包括：

​	**host**：请求域名或IP

​	**hostname**：服务器名称

​	**port**：请求端口

​	**method**：HTTP请求方法，默认是GET。（http.get时只能为"GET"）

​	**path**：请求的相对于根的路径，默认是'/'。QueryString应该包含在其中。例如：/index.html?page=12

​	**headers**：请求头对象

```js
const http = require('http');
const port = 3000;

const server = http.createServer((req,res) => {
    res.statusCode = 200;
    res.setHeader('Content-Type','text/plain;charset=utf-8');
    res.write('Hello')
    res.write('World')
    res.end('Wangcai');
})

server.listen(3000,() => {
    console.log('Start');
})

http.get('http://localhost:3000','',(res) => {
    console.log(res);
    let rawData = ''
    res.on('data', (data) => {
        rawData += data;
    })
    res.on('end', () => console.log(rawData))
})
```

![image-20240329151407460](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403291514520.png)

## fs

NodeJS中文件的操作，包括目录的创建、删除、查询以及文件的读写操作，在fs中，所有方法都分为同步和异步两种实现，具有sunc后缀的方法为同步方法，不具有的为异步方法。





### 1. 文件读取

```js
const fs = require('fs')

// 同步读取
let buf = fs.readFileSync('demo.txt','utf-8')
console.log(buf)

// 异步读取
fs.readFile('demo.txt', 'utf-8', (err,data) => {
    // console.log(err)  null
    console.log(data)
})
```

![image-20240329155545225](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403291555332.png)

### 2. 文件写入

```js
const fs = require('fs')

// 同步写入
fs.writeFileSync('demo.txt',"Hello,World!")
const data = fs.readFileSync('demo.txt','utf-8')
console.log(data)

// 异步写入
fs.writeFile('demo.txt',"Wangcai",(err) => {
    if(!err) {
        fs.readFile("demo.txt",'utf-8',(err,data) => {
            console.log(data)
        })
    }
})
```

![image-20240329160437885](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403291604940.png)

### 3. 追加写入

```js
const fs = require('fs')

// 同步追加写入
fs.appendFileSync('demo.txt',"Hahaha")
const data = fs.readFileSync('demo.txt','utf-8')
console.log(data)

// 异步追加写入
fs.appendFile('demo.txt',"456",err => {
    if(!err) {
        fs.readFile('demo.txt','utf-8',(err,data) => {
            console.log(data)
        })
    }
})
```

![image-20240329173357989](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403291733045.png)

### 4. 文件拷贝写入

```js
const fs = require('fs')

// 同步拷贝文件  目标文件不存在会自动创建
fs.copyFileSync('demo.txt','Wc.txt')
const data = fs.readFileSync('Wc.txt','utf-8')
console.log(data)

// 异步拷贝文件
fs.copyFile('demo.txt','Xx.txt',(err) => {
    if(!err) {
        fs.readFile('Xx.txt','utf-8',(err,data) => {
            console.log(data)
        })
    }
})
```

![image-20240329174412163](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403291744231.png)

### 5. 创建文件目录

```js
const fs = require('fs')
// 目录需一级一级创建，无目录时用./
// 同步创建文件目录
fs.mkdirSync("./conponents")
fs.mkdirSync("./conponents/jsx")

// 异步创建文件目录
fs.mkdir('./conponents/css',err => {
    if(!err) {
        console.log('end')
    }
})
```

![image-20240329175452542](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403291754598.png)

### 6. 创建文件

**使用fs.write()方法**

```js
const fs = require('fs')

fs.writeFile('conponents/jsx/test.jsx','',err => {
    if(!err) {
        fs.readFile('conponents/jsx/test.jsx','utf-8',(err,data) => {
            console.log(data)
        })
    }
})
```

![image-20240329175944129](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403291759181.png)

### 7. 读取文件目录

```js
const fs = require('fs')

// 同步读取文件目录，返回其子文件（目录）
const data = fs.readdirSync('./conponents/jsx')
console.log(data)

// 异步读取文件目录，返回其子文件（目录）
fs.mkdirSync('./conponents/css/a.css')
fs.mkdirSync('./conponents/css/b.css')
fs.writeFileSync('./conponents/css/c.css','')
fs.readdir('./conponents/css',(err,data) => {
    console.log(data)
})

// 肉眼无法分别结果为文件还是目录
```

![image-20240329180938259](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403291809324.png)

	### 8. 删除目录

**删除的目录需要为空**

```js
const fs = require('fs')

// 同步文件目录
fs.rmdirSync('./conponents/css/a.css')

// 异步删除文件目录
fs.rmdir('./conponents/css/b.css',err => {
    if(!err) {
        console.log('end')
    }
})
```

![image-20240329181704152](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403291817211.png)

### 9. 删除文件

**unlink**

```js
const fs = require('fs')

// 同步删除文件
fs.unlinkSync('./conponents/css/c.css')

// 异步删除文件
fs.unlink('./conponents/jsx/test.jsx',err => {
    if(!err) {
        console.log('end')
    }
})
```

![image-20240329195130442](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403291951506.png)

## PATH

**path模块提供函数来访问文件系统并与文化系统进行交互**



### 1. basename

**返回路径的最后一部分，第二个参数可以过滤后缀**

```js
const path = require('path')

const p = path.basename('index.txt')
const p1 = path.basename('index.txt.js','.js')
const p2 = path.basename('index.txt.js','.txt')
console.log(p, p1, p2)
```

![image-20240329214438043](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403292144113.png)

### 2. dirname 

**返回路径的目录部分**

```js
const path = require('path')

console.log(path.dirname('./a/b'))
console.log(path.dirname('./a/b/c.txt'))
console.log(path.dirname('info.jsx'))
```

![image-20240329214826746](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403292148809.png)

### 3. extname

**返回路径的扩展名（后缀部分）**

```js
const path = require('path')

console.log(path.extname('./a/b/wc.jsx'))
console.log(path.extname('./a/b/wc'))
// 无后缀为空
```

![image-20240329215141665](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403292151725.png)

### 4. isAbsolute 

**校验路径是否为绝对路径**

```js
const path = require('path')

console.log(path.isAbsolute('./a/b/wc.jsx'))
console.log(path.isAbsolute('/a/b/wc'))
```

![image-20240329215417002](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403292154061.png)

### 5. join 

**连接传入的多个路径**

```js
const path = require('path')

console.log(path.join('./a/b','c','name.js'))
const a = index.html
console.log(path.join('./a/b','d',a))
```

![image-20240329215833702](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403292158757.png)

### 6. normalize 

**矫正传入的路径**

```js
const path = require('path')

console.log(path.normalize('./a/b//c.css'))
console.log(path.normalize('./a/b//../d.css'))
```

![image-20240329220236281](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403292202358.png)

### 7. parse 

**解析路径将其转换为对象**

```js
const path = require('path')

console.log(path.parse('./a/b/c'))
console.log(path.parse('./a/b/d.css'))
```

![image-20240329220505937](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403292205000.png)

### 8. relative 

**相对于第一个参数的第二个参数文件的路径**

```js
const path = require('path')

console.log(path.relative('./a/b','a/b/c/info.js'))
```

![image-20240329220918863](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403292209938.png)

### 9. resolve 

**寻找指定参数的文件绝对路径**

```js
const path = require('path')

console.log(path.resolve('path.js'))
// 指定目录下寻找
console.log(path.resolve('conponents','path.js'))
```

![image-20240329221252652](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403292212712.png)

## 事件模块

events模块提供一个对象events.EventEmitter，EventEmitter核心是事件发射与事件监听器。

EventEmitter支持多个监听

### 1. addListener() / on()

**为事件注册一个监听**

参数1：事件名

参数2：回调函数

```js
const eventEmitter = require('events')
const door = new eventEmitter()

// addListener() 等价 on()
// 注册connection事件，执行函数为后面的回调函数
door.addListener('connection',() => {
    console.log('Hello')
})

// 事件调用
door.emit('connection')
```

![image-20240330141108795](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403301411859.png)



### 2.emit()

事件调用



### 3. once()

**事件注册后只能被首次调用一次，调用完成后被移除。**

```js
const eventEmitter = require('events')
const door = new eventEmitter()

door.once('click',() => {
    console.log('Hello')
})

door.emit('click')
door.emit('click')
door.emit('click')
```

![image-20240330141847843](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403301418890.png)

### 4. eventNames()

**获取对象身上所有的注册事件**

```js
const eventEmitter = require('events')
const door = new eventEmitter()

door.addListener('click',() => {
    console.log('Hello')
})

door.once('add',() => {
    console.log('Wangcai')
})

door.emit('click')
door.emit('add')
console.log(door.eventNames())
```

![image-20240330142317979](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403301423021.png)

### 5. removeListener()

参数1：要移除的事件名

参数2：事件名对应的回调函数（注册的事件）



**NodeJS中一个事件可以绑定多个函数，当事件调用时按顺序执行**

```js
const eventEmitter = require('events')
const door = new eventEmitter()


door.addListener('click',() => {
    console.log('Hello')
})

door.addListener('click',() => {
    console.log('Wangcai')
})

door.emit('click')
```

![image-20240330142707615](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403301427658.png)

```js
const eventEmitter = require('events')
const door = new eventEmitter()


door.addListener('click',() => {
    console.log('Hello')
})

let clickFun = () => {
    console.log('Wangcai')
}
door.addListener('click',clickFun)

console.log(door.eventNames())
door.emit('click')

door.removeListener('click',clickFun)
door.emit('click')
```

![image-20240330143529783](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403301435830.png)

```js
// 移除该事件上的所有函数
door.removeAllListeners('事件名')
```



### 6. listeners()

获取作为参数传入的事件监听器的数组

参数1：需要获取的事件名

```js
const eventEmitter = require('events')
const door = new eventEmitter()

door.addListener('getname',() => {
    console.log('Hello')
})

let getNameFun = () => {
    console.log('Haha')
}

door.addListener('getname', getNameFun)

console.log(door.listeners('getname'))

// 匿名函数为[Function (anonymous)]
```

![image-20240330144649053](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403301446096.png)

```js
const eventEmitter = require('events')
const door = new eventEmitter()

door.addListener('getname',() => {
    console.log('Hello')
})

let getNameFun = () => {
    console.log('Wangcai')
}

door.addListener('getname', getNameFun)

let FunList = door.listeners('getname')
FunList.forEach(element => {
    element()
})
```

![image-20240330144949308](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403301449356.png)

### 7. setMaxListeners()

设置可以添加到EventEmitter对象监听器的最大数量（默认为10，可以增加或减少）

```js
const eventEmitter = require('events')
const door = new eventEmitter()

door.setMaxListeners(1)
// 此时door对象只能注册1个事件监听，否则报错。
```

## buffer(缓冲区)

JavaScript 语言自身只有字符串数据类型，没有二进制数据类型。

但在处理像TCP流或文件流时，必须使用到二进制数据。因此在 Node.js 中，定义了一个 Buffer 类，该类用来创建一个专门存放二进制数据的缓存区。

*使用* **Buffer.from()** *接口去创建Buffer对象。*

```js
// 取Buffer对象
const Buffer = require('buffer').Buffer

// 通过form创建流
const buf = Buffer.from([0x68, 0x65, 0x6c, 0x6c, 0x6f])

console.log(buf)
```

![image-20240331135712687](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403311357747.png)

```js
const str = buf.toString('utf-8')
console.log(str)   //hello
```

![image-20240331135835197](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403311358247.png)

```js
const buf = Buffer.from('你好！')
console.log(buf.toString('utf-8'))
```

![image-20240331140038318](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403311400384.png)

### 1. alloc

创建固定大小的Buffer流空间

```js
const Buffer = require('buffer').Buffer

const buf = Buffer.alloc(3,'eve')
console.log(buf)
```

![image-20240331140428471](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403311404519.png)

```js
const Buffer = require('buffer').Buffer

// 写入字符超出设定时，取到设定的位置   小于设定时重复取到设定数
const buf = Buffer.alloc(3,'eve','utf-8')
console.log(buf.toString())

const buf1 = Buffer.allocUnsafe(3)  // 无设置默认值和指定编码格式权限
console.log(buf1)
```

![image-20240331140919742](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403311409794.png)

### 2. 数组格式

可读取和修改操作，按数组操作

```js
const Buffer = require('buffer').Buffer

const buf = Buffer.from('hello')
console.log(buf)
console.log(buf[0])
console.log(buf[1])
console.log(buf[2])
console.log(buf[3])
console.log(buf[4])
```

![image-20240331141837713](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403311418776.png)

```js
const Buffer = require('buffer').Buffer

const buf = Buffer.from('hello')
console.log(buf)
buf[0] = 111
console.log(buf)
console.log(buf.toString())
```

![image-20240331141941654](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403311419706.png)

### 3. 遍历

for循环和forEach都可

```js
const Buffer = require('buffer').Buffer

const buf = Buffer.from('hello')
buf.forEach(element => {
    console.log(element)
})
```

![image-20240331142316949](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403311423007.png)

### 4. 字符和字符串转换

```js
const Buffer = require('buffer').Buffer

const buf = Buffer.from('hello')
buf.forEach(element => {
    console.log(element)
    const buf = Buffer.from([element])
    console.log(buf.toString())
})
```

![image-20240331142812266](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403311428326.png)



```js
const Buffer = require('buffer').Buffer

const buf = Buffer.from('hello')

buf.write('wangcai')
console.log(buf.toString())
```

![image-20240331143119025](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403311431075.png)

### 5. copy

先分配相应大小

```js
const Buffer = require('buffer').Buffer

const buf = Buffer.from('hello')
const buf1 = Buffer.alloc(5)

console.log(buf1)
buf.copy(buf1)
console.log(buf1)
```

![image-20240331143724273](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403311437330.png)

### 6. 切片（弃用）

slice

参数1：起始位置

参数2：终止位置

左闭右开，不取第二个参数则切完

```js
xxx.slice(0,2)
```



## Stream 流

![image-20240331144536544](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403311445664.png)

### 1.读取流

![image-20240331150632702](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403311506763.png)

创建对象

```js
const Stream = require('stream')

// 创建读取流
const readableStream = new Stream.Readable()

readableStream._read = () => {};

// 监听
readableStream.addListener('data',(str) => {
    console.log(str.toString())
})


readableStream.push('Hello')
readableStream.push('wc')
```

![image-20240331151257061](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403311512123.png)

fs模块自带创建读取流

```js
const Stream = require('stream')
const fs = require('fs')

const info = fs.createReadStream('demo.txt')

info.addListener('open',() => {
    console.log('Start')
})

info.addListener('data',(str) => {
    // console.log(str.toString())
    console.log('读取中')
})

info.addListener('error', (err) => {
    console.log(err)
})

info.addListener('close', () => {
    console.log('读取完毕')
})

console.log('开始')
```

![image-20240331153055023](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403311530079.png)

### 2. 写入流

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403311533545.png" alt="image-20240331153321478" style="zoom:80%;" />

```js
const Stream = require('stream')

const writeSteam = new Stream.Writable()

writeSteam._write = (chunk,encoding,next) => {
    console.log(chunk.toString())
    console.log(encoding)
    next()
}

writeSteam.write('Hello,wc!', () => {
    console.log('write end')
})
```

![image-20240331154131378](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403311541432.png)

fs模块

**写入需在end前**

```js
// 可写入多次
const Stream = require('stream')
const fs = require('fs')

const fsW = fs.createWriteStream('writetest.txt')

const data = 'Hello'
fsW.write(data,'utf-8')
fsW.write('wc','utf-8')

fsW.end()

fsW.addListener('finish',() => {
    console.log('end')
})

fsW.addListener('error', (err) => {
    console.log(err)
})
```

![image-20240331163353819](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403311633887.png)

### 3. 可读写流

读写结合，将读传给写

读取流中的pipe管道可传入给写入流

```js
const Stream = require('stream')

const readStream = new Stream.Readable()
const writeStream = new Stream.Writable()

readStream._read = () => {}

writeStream._write = (chunk,encoding,next) => {
    console.log(chunk.toString())
    next()
}

readStream.pipe(writeStream)

// readStream.addListener('readable',() => {
//     console.log(readStream.read().toString())
// })

readStream.push('Haha')
readStream.push('asdfasdfasdfasdfasdfasdf')
```

![image-20240331210241071](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403312102147.png)

## Node特点

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403312104231.png" alt="image-20240331210409122" style="zoom: 67%;" />

## Node使用场景

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202403312109916.png" alt="image-20240331210957730" style="zoom:67%;" />

## -----------------------

## GET、POST请求





















# *Express*

## 1. 初识Express

```js
// 与http模块相似，封装
// 导入express
const express = require('express')

const app = express()

app.get('/', (req,res) => {
    res.statusCode = 200;
    res.setHeader('ContentType','text/plain;charset=utf-8')
    res.send('Hello,wangcai!')
})

app.get('/admin', (req,res) => {
    res.statusCode = 200;
    res.setHeader('ContentType','text/plain;charset=utf-8')
    res.send('后台')
})

// 监听
app.listen(3000, () => {
    console.log('Server Start')
})
```

## 2. Express路由

**客户端的请求与服务器处理函数之间的映射关系。**

**express路由由三部分组成：请求类型、请求的URL地址、处理函数。**

格式：

```js
const express = require('express')
const app = express()

app.method(PATH,HANDLER)
```

例子：

```js
const express = require('express')
const app = express()

// GET
app.get('/', (req,res) => {
    res.send('Hello,GET!')
})

// POST
// postman工具测试
app.post('/', (req,res) => {
    res.send({'name':'wc','age':18})
})

app.put('/', (req,res) => {
    res.send('Hello,PUT!')
})

app.delete('/', (req,res) => {
    res.send('Hello,DELETE!')
})


app.listen(3000, () => {
    console.log('Server Start')
})
```

![image-20240401201009745](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202404012010828.png)

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202404012010703.png" alt="image-20240401201023620" style="zoom:67%;" />

## 3. 模块化路由

**router.js**

```js
const express = require('express')

const router = express.Router()


// GET
router.get('/', (req,res) => {
    res.send('Hello,GET!')
})

// POST
router.post('/', (req,res) => {
    res.send({'name':'wc','age':18})
})

router.put('/', (req,res) => {
    res.send('Hello,PUT!')
})

router.delete('/', (req,res) => {
    res.send('Hello,DELETE!')
})

module.exports = router
```

**app.js**

```js
const express = require('express')
// 导入路由
const router = require('./router-demo.js')
const app = express()

//路由部分换成导入的
app.use(router)

app.listen(3000, () => {
    console.log('Server Start')
})
```

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202404012020868.png" alt="image-20240401202034790" style="zoom:67%;" />

## 4. 请求参数

```js
// POST
// 返回状态码201后再将json返回
router.post('/', (req,res) => {
    res.status(201).send({'name':'wc','age':20})
})
```

![image-20240401202411904](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202404012024968.png)

```js
router.get('/', (req,res) => {
    res.set() // 设置一个头部信息
    res.setHeader() // 设置一组头部信息
    res.status(201).send({'name':'wc','age':20})
    res.end() // 结束
})
```



```js
//路由部分换成导入的
app.use('/user', router) // 为所有路由加入上级前缀/user
```



发送GET请求并传入name，age参数

```js
router.get('/', (req,res) => {
	console.log(req.query.name)
    console.log(req.query.age)
    res.status(201).send({'name':'wc','age':20})
    res.end() // 结束
})
```

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202404012035679.png" alt="image-20240401203546476" style="zoom:80%;" />

## 5. 中间件

**请求到响应的中间过程，可以连续调用多个中间件**

![image-20240401210215023](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202404012102136.png)

```js
// app.js
const express = require('express')
// 导入路由
const router = require('./router-demo.js')
const app = express()

// 定义中间件,全局生效，所有请求都会执行该中间件
app.use((req,res,next) => {
    console.log('我先执行')
    next()
})

//路由部分换成导入的
app.use(router)

app.listen(3000, () => {
    console.log('Server Start')
})
```

![image-20240401210810066](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202404012108137.png)

局部路由：

```js
const express = require('express')

const app = express()

// 定义中间件
const fun = (req,res,next) => {
    console.log('我先执行')
    next()
}

// 只有该路由的GET请求执行fun中间件，多个用[]
app.get('/',fun,(req,res) => {
    res.send('haha')
    console.log('我后执行')
})

app.listen(3000, () => {
    console.log('Server Start')
})
```

![image-20240403235400329](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202404032354415.png)



![image-20240403235705095](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202404032357172.png)

![image-20240403235723567](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202404032357630.png)

![image-20240403235751754](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202404032357846.png)

![image-20240403235820094](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202404032358196.png)

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202404040000393.png" alt="image-20240404000007286" style="zoom:67%;" />

![image-20240404000657558](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202404040006669.png)

***express.static()***

静态资源托管

```js
// 除错误中间件外，其余中间件需在路由前配置

app.use(express.内置中间件)
app.use(express.static('./resource'))  // 静态资源托管，该目录下资源都能进行访问，应使用static命名更合理

app.listen(3000, () => {
    console.log('Server Start http://localhost:3000/index.html')
})
```

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202404040013683.png" alt="image-20240404001341636" style="zoom: 67%;" />

<img src="https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202404040014203.png" alt="image-20240404001405075" style="zoom:50%;" />

***express.json()***

解析json格式的请求体数据

```js
const express = require('express')

const app = express()

app.use(express.json())


app.get('/',(req,res) => {
    console.log(req.body)  // 接收请求体数据，不做处理时默认为undefined
    res.send('get')
})

app.post('/',(req,res) => {
    res.send('post')
})

app.use(express.static('./resource'))  // 静态资源托管,该文件夹下的资源都能被访问
app.listen(3000, () => {
    console.log('Server Start http://localhost:3000/index.html')
})
```

![image-20240404003224582](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202404040032632.png)



![image-20240404003236441](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202404040032487.png)

***express.urlencoded()***

解析URL-encoded格式的请求体数据

```js
const express = require('express')

const app = express()

app.use(express.json())
app.use(express.urlencoded({extended: false}))

app.get('/',(req,res) => {
    console.log(req.body)  // 接收请求体数据，不做处理时默认为undefined
    res.send('get')
})

app.post('/',(req,res) => {
    console.log(req.body)  // 接收表单请求体数据，不做处理时默认为undefined
    const {name, age} = req.body
    console.log('name:',name)
    console.log('age:',age)
    res.send('post')
})

app.use(express.static('./resource'))  // 静态资源托管,该文件夹下的资源都能被访问
app.listen(3000, () => {
    console.log('Server Start http://localhost:3000/index.html')
})
```

![image-20240404005545357](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202404040055402.png)

## 6. 连接数据库

sqlpub：

名称：wcdesql

用户：wangcai

密码：xxxx

地址：mysql.sqlpub.com:3306

数据库工具：navicat

**测试demo：**

```js
// 安装mysql
cnpm i mysql --save
```

```js
const express = require('express')
const mysql = require('mysql')
const bodyParser = require('body-parser')
const cors = require('cors')

const app = express()
app.use(bodyParser.json())
app.use(cors())

// 创建mysql连接
const connection = mysql.createConnection({
    host: 'mysql.sqlpub.com',
    user: 'wangcai',
    password: '5bQA7dF39bfUjCFs',
    port: '3306',
    database: 'wcdesql'
})

connection.connect();

const sql = "select * from student"; // 执行查询语句

connection.query(sql,(err,result)=>{
    if(err) {
        console.log(err);
        return
    }
    app.get('/api',(req,res) => {
        res.send(result)
    })

    app.post('/api',(req,res) => {
        res.send(result)
    })

    app.listen(3000, () => {
        console.log('Server Start:','http://localhost:3000/api')
    })

    connection.destroy(); // 释放资源
})

connection.end(err => {
    if(err) {
        console.error('Error')
        return
    }
    console.log('MySQL closed')
})
```

![image-20240404160923526](https://blog-wc-imgs.oss-cn-chengdu.aliyuncs.com/imgs/md/202404041609614.png)

## 7. API

连接池：**sequelize**

```js
```

































## 8. Express-validator

**express-validation是一个中间件，它验证请求的body, params, query, headers 和 cookies ，并且如果任何配置的验证规则失败,返回一个错误的响应**

安装

```js
cnpm i express-validator
```

在发起请求的路由位置引入body、validationResult

用在路由请求的第二个参数位置























## 9. 模板引擎









### 1. EJS















### 2. PUG













## 10. Socket通讯

WebSocket整体通讯的流程就是 **建立链接->发送消息->关闭链接/终止链接**

不管客户端还是服务端WebSocket的核心事件分为两类，一类是监听事件、一类是触发事件

**监听事件**

监听事件主要就是以下四类，在服务端跟客户端都通用

onOpen：监听连接建立的消息

onMessage：监听双端发送的消息

onClose：监听连接断开的消息

onError：监听异常发生的消息



**触发事件**

触发事件主要就是发送消息跟断开连接需要触发，也是客户端跟服务端都通用

send：主动发送消息的事件

close：主动关闭连接的事件



