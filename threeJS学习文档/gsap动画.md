# gsap基础

## 安装gsap

```
npm install gsap
```

gsap文档：[gsap - npm (npmjs.com)](https://www.npmjs.com/package/gsap)

## 动画设置

#### 创建一个动画

```javascript
//cube为先前定义好的一个物体，position为需要控制的运动类型，position为移动类型（rotation，scale...）
var animate1 = gsap.to(cube.position, {
    // 移动方向和距离
    x: 5,
    // 持续时间
    duration: 2.5,
    // 过渡动画
    ease: "power1.inOut",
    // 动画重复次数，-1为无限循环
    repeat: -1,
    // yoyo为true，表示从结尾倒退到开头往返循环运动
    yoyo: true,
    // onComplete(),动画结束回调函数，repeat为-1时不生效
    onComplete() {
        console.log("动画完成")
    },
    onStart() {
        console.log("动画开始")
    }
});
```

#### 控制动画属性

```javascript
//动画是否处于运动状态，由pause和resume决定
animate1.isActive(); //true/false
//调用后控制动画运动的暂停
animate1.pause(); 
//调用后恢复动画的运动
animate1.resume();
```

