#$(document).ready()方法, onload事件 , $(window).load()方法 

## window.onload事件是在整个页面包括dom结构、图片等等全部加载完成之后才会触发

## $(document).ready()是在DOM结构绘制完毕之后就执行内部的语句了，不用像window.onload一样，需要等到全部元素都加载完毕才执行。
## $(window).load()是Jquery中的一个方法，效果等同onload事件