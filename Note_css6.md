## 进阶

### 精灵图

一个网页中往往会有很多小背景图作为装饰，但是网页中图像较多的时候，服务器会频繁接收和发送请求图片，造成服务器压力过大，降低页面加载速度。由此出现了CSS 精灵技术。

核心原理：将网页中的一些小背景图像整合到一张大图中，这样服务器只需要一次请求就可以了。