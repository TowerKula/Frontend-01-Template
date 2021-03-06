# 第四周总结

## 结构化程序设计与执行过程
* 事件循环(eventLoop)
    1. 事件循环既不属于js语言，也不属于js引擎。
    2. 事件循环属于浏览器、nodejs等宿主环境的一部分。提供给调用方使用js的功能。
* promise 是JS标准里的内容
* 宏任务与微任务的总结归纳
    1. 离开JS引擎执行的是宏任务。
    2. 在JS引擎内执行的是微任务。
    3. eval、setTimeout、setInterval、script标签、click等浏览器事件 均属于宏任务。
    4. promise 属于微任务。
* 参考极客时间-李兵老师的浏览器工作原理及v8引擎解析：
    1. 微任务队列执行在当前宏任务的主进程全局上下文中，所以只有当前宏任务下的所有微任务结束才能释放整个上下文环境，读取下一个宏任务。
    2. async/await 是通过协程间切换配合promise微任务实现的，虽然切换协程，但微任务还是挂载到主进程下，所以执行效果与winter老师的解释一致。
    3. winter老师的微任务概念比较抽象，并不针对promise形成的微任务队列进行描述，他的微任务涵盖所有宏任务下待执行的子语句。