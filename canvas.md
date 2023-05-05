# 基础

# 实践

### 如何将一个图片按照canvas绘画好的形状显示( ctx.clip（），ctx.drawImage(image) ），并将该canvas设为全局的背景？

```
context.drawImage(img,sx,sy,swidth,sheight,x,y,width,height);
```

| 参数      | 描述                                         |
| :-------- | :------------------------------------------- |
| *img*     | 规定要使用的图像、画布或视频。               |
| *sx*      | 可选。开始剪切的 x 坐标位置。                |
| *sy*      | 可选。开始剪切的 y 坐标位置。                |
| *swidth*  | 可选。被剪切图像的宽度。                     |
| *sheight* | 可选。被剪切图像的高度。                     |
| *x*       | 在画布上放置图像的 x 坐标位置。              |
| *y*       | 在画布上放置图像的 y 坐标位置。              |
| *width*   | 可选。要使用的图像的宽度。（伸展或缩小图像） |
| *height*  | 可选。要使用的图像的高度。（伸展或缩小图像） |

```html
//body
//首先定义一个canvas，设置canvas样式 position:absolute;z-index:-1 即可将该canvas设置成全局的背景
<canvas id="c1" width="600" height="400" style="position:absolute;z-index:-1">
        当前浏览器不支持canvas，请下载最新的浏览器
        <a href="http://">立即下载</a>
</canvas>
```

```javascript
//script
//绘制好需要的图形
		/** @type {HTMLCanvasElement} */
        var c1 = document.getElementById('c1')
        var ctx = c1.getContext('2d')
        
        ctx.beginPath();
        ctx.moveTo(200,300) //起点位置第一个点
        ctx.quadraticCurveTo(150,300,150,200)
        ctx.quadraticCurveTo(150,100,300,100)
        ctx.quadraticCurveTo(450,100,450,200)
        ctx.quadraticCurveTo(450,300,250,300)
        ctx.quadraticCurveTo(250,350,150,350)
        ctx.quadraticCurveTo(200,350,200,300)

        ctx.stroke() //显示
        ctx.closePath()
//绘制好图形后，创建一个image对象，将图片地址赋值给image对象的src属性中，即可访问到该图片
        image = new Image();
        image.src = "http://www.designerspics.com/wp-content/uploads/2015/03/time_alone3_free_photo.jpg";
//实现该效果的前提是图片先加载完成，图片加载完成后，
        image.onload = function () {
//clip() 方法从原始画布中剪切任意形状和尺寸。
//提示：一旦剪切了某个区域，则所有之后的绘图都会被限制在被剪切的区域内（不能访问画布上的其他区域）。您也可以在使用 clip() 方法前通过使用 save() 方法对当前画布区域进行保存，并在以后的任意时间对其进行恢复（通过 restore() 方法）。
            ctx.clip();
//ctx.drawImage(image) 裁剪好后将上传的图片画入裁剪的图形中
            ctx.drawImage(image,0,0);
        }
```



### 实现如下背景效果（图片嵌入图形，图片向上渐变透明）

![image-20230428110614132](C:\Users\kangkanglaize\AppData\Roaming\Typora\typora-user-images\image-20230428110614132.png)
