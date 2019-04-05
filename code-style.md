# JS
## **[强制]** **变量名使用有意义的英文单词组成，不得使用拼音**

```javascript
// bad
const xiangmuming = 'test'

// good
const projectName = 'test'
```

## **[强制]** **类采用大驼峰式命名，方法、函数、变量使用小驼峰式命名**
```javascript
class Person {
  makeMoney(money){
    const computedMoney = money * 1000000;
  }
}
```

## **[强制]** **常量使用大写单词加下划线**
```javascript
const MAX_THRESHOLD = 10
```

## **[强制]** **私有方法或者属性使用下划线开头**
```javascript
class Person {
  constructor() {
    this._money = 0;
  }

  _getBalance() {
    return 0;
  }
}
```

## **[强制]** **函数开头必须是有意义的动词或动词短语**

## **[强制]** **布尔值变量或者返回值为布尔值的函数使用 is、can、has、should 开头**
```javascript
const isTrue = true;
const hasEven = function() {}
```

## **[强制]** **使用两个空格缩进**

## **[强制]** **变量尽量使用 const 定义，需要改变的变量使用 let，不要使用 var 定义变量**

## **[强制]** **`{` 前不要换行**
```javascript
// bad
function f() 
{
  ...  
}

if () 
{
  ...
} 

// good
function f() {
  ...
}
if () {
  ...
}
```

## **[强制]** **一元运算符与操作对象之间不允许有空格，二元操作符与操作对象之间必须有空格**
```javascript
// bad
const a = '1';
const b = + a;
const c = b ++;
const d = 1+2*3;

// good
const a = '1';
const b = +a;
const c = b++;
const d = 1 + 2 * 3;
```

## **[建议]** **对同一变量的多种值进行判断时，可以将 if 语句、switch 语句改为使用对象**
```javascript
function f(a) {
  let b;
  ...
  if(a === 1) {
    b = c;
  } else if(a === 2) {
    b = d;
  } else if(a === 3) {
    b = e;
  } else {
    b = a;
  }
}

function f(a) {
  let b;
  ...
  switch (a) {
    case 1: 
      b = c; break;
    case 2: 
      b = d; break;
    case 3: 
      b = e; break;
    default:
      b = a; break;
  }
}

// better
function f(a) {
  let b;
  ...
  const map = {
    1: c,
    2: d,
    3: e,
    default: a
  };
  b = map[a] || map.default;
}
```

## **[强制]** **switch 语句不要穿透，case 后一定要跟 break，必须要有 default**

## **[强制]** **用作代码块起始的 `{` 前必须有空格**
```javascript
// bad
function f(){
  ...
}
if (){
  ...
}

// good
function f() {
  ...
}

if () {
  ...
}
```

## **[强制]** **if、else、for、while、function(非匿名函数)、switch、do、try、catch、finally 关键字后，必须有一个空格**
```javascript
if ()
else {}
while ()
for ()
function f(){}
const f = function() {}
switch () {}
do {}
try {} catch () {} finally {}
```

## **[强制]** **else、else if 不要换行**
```javascript
// bad
if() {
  ...
}
else {
  ...
}

// good
if() {
  ...
} else {
  ...
}
```

## **[强制]** **函数不要过长，尽量控制在 60 行以内**

## **[强制]** **使用字面量来创建对象或者数组**
```javascript
//bad
const obj = new Object();
const arr = new Array(5);

// good
const obj = {};
const arr = [];
```

## **[强制]** **对象和数组最后一项之后不允许有逗号**
```javascript
// bad
const obj = {
  a: 1,
  b: 2,
};

const arr = [1, 2,];

// good
const obj = {
  a: 1,
  b: 2
};

const arr = [1, 2];
```

## **[强制]** **对象、数组、函数形参列表每项的逗号后面都要有空格**
```javascript
// bad
const arr = [1,2,3];
const obj = { a: 1,b: 2 };
function f(a,b,c) {
  ...
}
f(a,b,c);

// good
const arr = [1, 2, 3];
const obj = { a: 1, b: 2 };
function f(a, b, c) {
  ...
}
f(a, b, c);
```

## **[强制]** **对象键后面不允许有空格，值前面要有空格**
```javascript
// bad
const obj = {
  a :1,
  b : 2
};

// good
const obj = {
  a: 1,
  b: 2
};
```

## **[强制]** **写在一行时，对象的括号与键值对之间要有空格**
```javascript
// bad
const obj = {a: 1, b: 2};

// good
const obj = { a: 1, b: 2 };
```

## **[强制]** **写在一行时，数组、对象的属性引用、函数形参列表与括号之间不允许有空格**
```javascript
// bad
const arr = [ 1, 2, 3 ];
const attr = obj[ 'test' ];
function f( a, b, c ) {
  ...
}
f( a, b, c );

// good
const arr = [1, 2, 3];
const attr = obj['test'];
function f(a, b, c) {
  ...
}
f(a, b, c);
```

## **[建议]** **浅拷贝数组或者对象使用 ... 展开运算符**
```javascript
const a = [1, 2, 3];
const o = { a: 1, b: 2 };
const arr = a.slice();
const obj = Object.assign({}, o, { c: 3 });

// better
const arr = [...a];
const obj = { ...o, { c: 3 } };
```

## **[建议]** **转换为数组时，可迭代对象使用 ... 展开运算符，不可迭代的类数组对象使用 Array.from**
```javascript
// 可迭代对象指可以使用 for...of 循环遍历的对象( 实现了Symbol.iterator 函数的对象 )
const arrLike = {
  0: 1,
  1: 2,
  length: 2
};
const s = new Set([1, 2, 3]);
const nodes = document.querySelectorAll('div');
const sets = [...s];
const nodesArr = [...nodes];
const arr = Array.from(arrLike);

```

## **[建议]** **尽量使用数组的高级函数来遍历数组(map、filter…)，对象使用Object.keys()、Object.values()、Object. entries () 生成的数组来进行遍历**
```javascript
const even = [1, 2, 3].filter(num => num%2 === 0);
const keys = Object.keys({ a: 1, b: 2 });
for (let key of keys) {
  ...
}
```

## **[强制]** **不要使用关键字或者保留字作为函数形参名**
```javascript
// bad
function f(a, arguments) {
  ...
}
```

## **[强制]** **使用剩余参数语法代替 arguments**
```javascript
// bad
function f(a) {
  const rest = Array.prototype.slice.call(arguments, 1);
  ...
}

// good
function f(a, ...rest) {
  ...
}
```

## **[强制]** **使用函数的默认参数，默认参数在后面**
```javascript
// bad
function f(a) {
  a = a || 'default';
}

// good
function f(b, a = 'default') {
  ...
}
```

## **[强制]** **使用解构赋值获取对象属性**
```javascript
// bad
const firstName = obj.firstName;
const lastName = obj.lastName;

// good
const { firstName, lastName } = obj;
```

## **[强制]** **当一行过长时，适当换行，换行时运算符必须在行首，逗号不允许换行在行首**
```javascript
// bad
function f(
  aaaaaaaaaaaa
  , bbbbbbbbbbbb
  , cccccccccccc
) {
  if(
    aaaaaaaaaaa &&
    bbbbbbbbbbb &&
    ccccccccccc
  ) {
    const computed = aaaa + bbbb + ccccc +
      dddd + eeee;
    const larger = computed + 1000000000000 > 10000 ?
      10 : 20; 
  }
}

// good
function f(
  aaaaaaaaaaaa,
  bbbbbbbbbbbb,
  cccccccccccc
) {
  if(
    aaaaaaaaaaa 
    && bbbbbbbbbbb
    && ccccccccccc
  ) {
    const computed = aaaa + bbbb + ccccc 
      + dddd + eeee;
    const larger = computed + 1000000000000 > 10000 
      ? 10 : 20; 
  }
}
```

## **[强制]** **在 if、else、for、do、while 语句中，即使只有一行，也不得省略块 {…}**
```javascript
// bad
if () a += 1;
for () a += 1;

// good
if () {
  a += 1;
}
for () {
  a += 1;
}
```

## **[强制]** **字符串都必须使用单引号**
```javascript
// bad
const a = "test";

// good
const a = 'test';
```

## **[强制]** **使用模板字符串代替字符串拼接**
```javascript
// bad
const str = 'test' + a;

// good
const str = `test${a}`;
```
## **[强制]** **禁止使用链式赋值**
```javascript
// bad
let a = b = c = 10;
```

## **[强制]** **禁止使用 ==、!=，使用 ===、!==**

## **[强制]** **基本类型检测使用 typeof，对象使用 instanceof，null、undefined使用 == null**

## **[强制]** **三目运算符不允许嵌套**

## **[强制]** **多个逻辑运算符使用圆括号表明逻辑**
```javascript
// bad
const a = a && b || c && d;

// good
const a = (a && b) || (c && d);
```

## **[强制]** **不要使用逻辑运算符控制代码执行**
```javascript
// bad
!a && b()

// good
if (!a) {
  b();
}
```

## **[强制]** **使用 Number.isNaN 代替 isNaN**

## **[强制]** **使用 Math.floor 等方法将小数化整，不要使用 parseInt**

## **[强制]** **parseInt 必须传第二个参数**

## **[强制]** **如果常量的意图不明显，使用变量命名常量**
```javascript
// bad
const average = total / 300;

// good
const fiveMinutes = 300;
const average = total / fiveMinutes;
```

## **[强制]** **除非必要，否则使用箭头函数来绑定 this**

## **[强制]** **import 语句后必须有分号**

## **[强制]** **import 语句过长时，必须格式化**

## **[强制]** **非行首单行注释前必须空行，单行注释必须独占一行，不可以写在语句后面，双斜线后必须有空格**
```javascript
// bad
function f() {
  ...
  // comment
  const a = 1; // comment
}

// good
function f() {
  ...

  // comment
  const a = 1;
}
```

# HTML

## **[强制]** **使用两个空格缩进**

## **[强制]** **嵌套代码必须缩进**

## **[强制]** **特性使用双引号**
```html
<div class="test"></div>
```

## **[强制]** **属性名小写，多个单词使用中划线 `-` 分隔**

## **[强制]** **不要在自闭合标签末尾使用反斜线**
```html
// bad
<img src="" />

// good
<img src="">
```

## **[强制]** **特性声明顺序**
```
class
id
name
data-*
src,  href,  type, value, for, max-length, max, min, pattern
placeholder, title, alt
required, readonly, disabled
```

## **[强制]** **boolean 类型特性不需要指定所取值**
```html
// bad
<input disabled="disabled">

// good
<input disabled>
```
## **[强制]** **避免多余的父节点元素，减少文档中的元素数量**


# CSS

## **[强制]** **使用两个空格缩进**

## **[强制]** **选择器、规则块起始花括号后要有空格**
```html
// bad
.test,.test1,test2{
  ...
}

.test>.test1 {
  ...
}

.test+.test1 {
  ...
}

.test~.test1 {
  ...
}

// good
.test, .test1, .test2 {
  ...
}

.test > .test1 {
  ...
}

.test + .test1 {
  ...
}

.test ~ .test1 {
  ...
}
```

## **[强制]** **每个规则块后要有换行**
```html
// bad
.test {
  ...
}
.test1 {
  ...
}

// good
.test {
  ...
}

.test1 {
  ...
}
```
## **[强制]** **需要使用引号的地方使用双引号**

## **[强制]** **使用 /\* \*/ 注释**

## **[强制]** **规则声明顺序**
```
布局类：display、float、position、left、top、right、bottom、overflow

盒模型类：width、height、margin、border、padding 等

文本类： font-*、line-height、text-align、word-wrap 等

显示类：color、background-*、transition、animation、list-style、opacity 等
```

## **[强制]** **颜色使用十六进制小写，能简写必须简写，不允许使用具名颜色**

## **[建议]** **尽量不要使用属性简写，例如：font**

## **[强制]** **scss 中选择器嵌套不能超过 5 层**

## **[强制]** **当值为小于 1 的小数时，省略整数部分**
```css
transition: 0.5s   =>   transition: .5s
```

## **[强制]** **长度为 0 时，省略单位**


# Vue

## **[强制]** **组件名必须使用大驼峰式命名，引入组件时也必须使用大驼峰式命名引入**

## **[强制]** **模板中使用大驼峰式命名，当组件没有 slot 需要传入时，使用单闭合标签写法**
```html
<MyComponent />
```

## **[强制]** **除了根实例，组件的 data 选项必须是函数，并且返回一个对象**

## **[强制]** **prop 定义尽量详细**
```javascript
// bad
prop: ['count']

// better
prop: {
  count: Number
}

// better
prop: {
  count: {
    type: Number,
    required: true
  }
}
```

## **[强制]** **模板中绑定 prop 使用中划线 `-` 分隔，定义时使用小驼峰式定义**
```javascript
// 定义
prop: {
  myProp: {
    type: Boolean,
    required: true
  }
}

// 绑定
<MyComponent :my-prop="true"/>
```

## **[强制]** **不要传入复合 prop，尽量传入单值 prop**
```html
// bad
<MyComponent :my-props="{ count: 1, show: true }"/>

// good
<MyComponent :count="1" :show="true"/>
```

## **[强制]** **v-for 必须指定 key**

## **[强制]** **v-for 与 v-if 不允许同时出现，使用计算属性过滤数据**

## **[强制]** **模板中，组件有多个特性或者绑定多个 prop、事件时，每个特性都需要换行**
```html
<MyComponent 
  :count="1"
  :show="true"
/>
```

## **[强制]** **模板中不应该包含逻辑，逻辑放到计算属性或者方法中**

## **[强制]** **组件实例选项声明顺序**
```
el
name
directives
filters
mixins
props
data
computed
watch
生命周期钩子函数
methods
template/render
```

## **[强制]** **模板中特性声明顺序**
```
is
v-for
v-if、v-else、vielse-if、v-show
v-once
class
id
ref、key、slot
v-model
其他特性
v-on
v-html、v-text
```

## **[强制]** **单文件组件标签顺序：template、script、style**

## **[强制]** **不允许在子组件中更改父组件的状态**

## **[强制]** **尽量不要在组件方法中进行 DOM 操作**

## **[强制]** **目录结构**
```
+ build: webpack 相关
+ src
    + assets
        + css
        + img
        + js: 三方库、工具方法
    + components
    + router
    + store
        index.js
        actions.js: 全局 action
        mutations.js: 全局 mutation
        + modules
    + api
    + mixins
    + filters
    + directives
    App.vue
    main.js
.babelrc
pacaage.json
index.html
```

# 编辑器

## 推荐使用 Visual Studio Code

```
推荐插件：
Auto Rename Tag
Bracket Pair Colorizer
Chinese(Simplified)
Javascript(ES6) code snippets
open in browser
Prettier
Vetur
```