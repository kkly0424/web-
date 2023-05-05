# jichu

### 深拷贝和浅拷贝

对于对象的复制，分为浅拷贝和深拷贝：

**浅拷贝：**（let newObj  = obj;)浅拷贝复制的是对象的引用地址，没有开辟新的栈，复制的结果是两个对象指向同一个地址，所以修改其中一个对象的属性，另一个对象的属性也跟着改变了。

**深拷贝：**( let newObj = JSON.parse(JSON.stringify(obj)); )深拷贝会开辟新的栈，两个对象对应两个不同的地址，修改对象A的属性，并不会影响到对象B。

**深拷贝方法：**

​	1.JSON.parse(JSON.stringify(obj)); //将对象转换为字符串，再把字符串转换为新的对象。使用于多层对象属性的对象；

​	2.对于无对象属性的数组：let newObj = [...obj]; 



### 事件循环

[JavaScript事件队列的宏任务与微任务 - 掘金 (juejin.cn)](https://juejin.cn/post/7001802155615059982)

JavaScript是单线程、无阻塞的。

**执行栈和事件队列：**

​	同步代码的执行，按顺序添加到执行栈中；

​	在遇到异步代码时，会将该异步代码任务放到事件队列中，等执行栈中所有同步任务都执行完毕后，按先进先出原则，将事件队列中的异步任务提到执行栈中执行；

**宏任务和微任务：**

​	同步代码执行完毕后，执行事件队列中的异步任务，`事件循环`检查当前事件队列时，首先检查当前`微事件队列`是否有任务，如果有则添加到当前执行栈执行，当执行完毕后再次检查，直到当前`微事件队列`为空后，再检查当前`宏事件队列`是否有任务，如果有则添加到当前执行栈执行。

<img src="https://img-blog.csdnimg.cn/2021070213542153.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L05hbmN5Rnlu,size_16,color_FFFFFF,t_70" alt="在这里插入图片描述" style="zoom: 67%;" />



**宏任务和微任务有哪些**：

以下事件属于宏任务：

- setInterval()

- setTimeout()

以下事件属于微任务：

- promise.then()
- Async/Await(实际就是promise)
- new MutaionObserver()

### Cookie

Cookie只能存储字符串型式的数据，若强行存储对象类型的数据则会强制转换为字符串[Object,object];