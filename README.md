
/*DOM在实际开发中是如何应用*/
<!DOCTYPE html>
<html>
<head>
	<title>slide</title>
	<link rel="stylesheet" type="text/css" href="reset.css">
  <link rel="stylesheet" type="text/css" href="css/style01.css">
	<script src="js/script01.js"></script>
</head>
<body>
<div id="container">
<img src="images/door1.png" alt="1080p" title="1080p">
<img src="images/door2.png" alt="5.5寸四核" title="5.5寸四核">
<img src="images/door3.png" alt="4寸五核" title="4寸五核">
<img src="images/door4.png" alt="5.7寸机皇" title="5.7寸机皇">
	
</div>
</body>
</html>
/*css*/

#container{
	height: 477px;
	margin: 0 auto;
	border-right: 1px solid #ccc;
	border-bottom: 1px solid #ccc;
	overflow: hidden;
	position: relative;
}
#container img{
  position: absolute;
  display: block;
  left: 0;
  border-left: 1px solid #ccc;
}
/*js*/
window.onload=function() {
	//获取容器
	var box=document.getElementById('container');
	//获得图片NodeList对象集合
	var imgs=box.getElementsByTagName('img');
	//获取单张图片的宽度
	var imgWidth=imgs[0].offsetWidth;
	//设置后面图片掩藏的宽度
	var exposeWidth=160;
	//设置所有图片展开容器的宽度
	var boxWidth=imgWidth+(imgs.length-1)*exposeWidth;
	box.style.width=boxWidth+'px';
	//设置每张要划动图片的初始位置
	function setImgsPos(){
	for(var i=1,len=imgs.length;i<len;i++){
		imgs[i].style.left=imgWidth+exposeWidth*(i-1)+'px';
    } 
}
    //图片滑动时移动的距离
     var translate=imgWidth-exposeWidth;
     //为图片滑动绑定事件
     for(var i=0,len=imgs.length;i<len;i++)	{
     	//使用立即调用的函数表达式，为了获得不同的i值
     (function(i){
         imgs[i].onmouseover=function(){
         	//先将每张图片复位
         	setImgsPos();
         	//打开图片
         	for(var j=1;j<=i;j++){
         		imgs[j].style.left=parseInt(imgs[j].style.left,10)-translate+'px';
         	}
         };
    })(i);
     }
	
};







