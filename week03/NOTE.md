# 第三周总结
Javascript 纲要：
*  `Atom`：构成语句的原子性元素，上周主要内容
*  `Expression`：构成核心计算的表达式，本周重点内容
*  `Statement`：控制程序结构和逻辑的语句，本周重点内容
*  Structure
*  Program/Module

## Expression
表达式的语法通常会解析成树结构，运算符优先级使用表达式生成树实现。
### Member Expression
* 解释：取属性操作、member访问
* 组成：
```js
    a.b , a[b] , 
    foo`string` //可以使用自定义函数处理template模板，进行DSL开发 
    super.b , 
    new.target //可以判断函数是否被 new 调起的，在函数内部使用。
```
* 返回：Reference 类型对象（由Object、可以构成）

### New Expression
*  举例：`new Foo`
### Call Expression
*  举例：
```js
foo();
super();
foo().b;
foo()`abc`
```
### Left handSide & right handSide
* 解释：以上表达式均属于左手表达式
* 右手表达式：包括 UpdateExpression、UnaryExpression 等等
* 举例：
```js
Unary:{//单目运算
    delete a.b
    void foo()
    typeof a
    +a
    -a
    ~a
    !a
    await a
}
```
>tips:
>1. 使用void 0 替代 undefined
>因为void 后接任何值都可以返回标准undefined对象
>2. IIFE使用void 开头，可以完整语义、调整格式结构，避免编译错乱
>void function(i){...}(i);
>3. 变量类型拆箱时，除特殊指定hint展示，一般按照symbol.toPrimitive() => valueOf => toString() 的顺序进行拆箱
## Statement
### Runtime（运行内部类型）
* 分类：completion record(语句执行完成结果描述) 、 lexical environment
* Completion Record ：
    1. [[type]] : normal break continue return throw -- 针对常见语句、和特定结束终止返回
    2. [[value]] : Types -- 有值类型返回
    3. [[target]] :label -- 针对有迭代的跳转结构返回

### 简单语句
* ExpressionStatement: 表达式语句“a=1+2;”
* EmptyStatement: 形如：“;”
* DebuggerStatement: 预留给调试的中断，“debugger”
* ThrowStatement: “throw a;”
* ContinueStatement:“continue”
* BreakStatement:“break;”
* ReturnStatement:“return 1+2;”

### 复合语句
* BlockStatement:返回类型=>[[type]] -- normal
* Iteration : 根据`[[target]]:label` 执行消费
* ... 同类复合语句还有很多

### 声明
* Function Declaration -- 仅作为举例
* ... 同类声明语句还有很多

## 结构化编程
* 为语言提供各种表达能力，是开发者能更接近自然思维的表达。
* 语言中的模仿，应该是模仿语言表达能力与结构，如模仿函数式编程，箭头函数等等。而不应是用js的原型能力去模仿基于类的面向对象。

## 面向对象
* 面向对象的基础三要素：唯一性、有状态、有行为。
* 面向对象的实现方式可以有多种（也叫实现范式）：java是基于“归类”的面型对象（对已有对象的归纳，可以同时属于多个类），而js采用的基于“分类”原型的分类（要么属于这个类，要么属于另一个类，只有一个原始父类）
* 对象的划分：行为函数的归属应该在于能否改变对象自身的状态。举例：狗咬人，那么“咬”这个行为在划分时应该放到“人”这个类中，因为改变的是“人”的状态。


