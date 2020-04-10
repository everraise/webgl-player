


#### demo ####
1.编辑器打开three.js项目。项目在路径apache-tomcat-9.0.31\webapps\three.js下
2.进入项目，本地打开在Test1目录下的class1.html,可以直接本地chrome打开。
3.也可以用tomcat访问下面有使用介绍。

### flv.js ###

在js中引入flv.js
```$xslt
<script src="flv.min.js"></script>
```
```javascript
video = document.getElementById( 'videoElement' );
		// video.play();
		if (flvjs.isSupported()) {
			var flvPlayer = flvjs.createPlayer({
				type: 'flv',
				url: 'url'//添加路由
			});
			flvPlayer.attachMediaElement(videoElement);
			flvPlayer.load(); //加载
		}
		//创建纹理视频
		texture = new THREE.VideoTexture( video );

```


### 调用摄像头 ###
注意：摄像头需要开启浏览器权限，备注掉flv.js部分代码。
```javascript
	//调用摄像头

 window.addEventListener( 'resize', onWindowResize, false );

 if ( navigator.mediaDevices && navigator.mediaDevices.getUserMedia ) {

 	var constraints = { video: { width: 1280, height: 720, facingMode: 'user' } };

 	navigator.mediaDevices.getUserMedia( constraints ).then( function ( stream ) {

 		// apply the stream to the video element used in the texture

 		video.srcObject = stream;
 		video.play();

 	} ).catch( function ( error ) {

 		console.error( 'Unable to access the camera/webcam.', error );

 	} );

 } else {

 	console.error( 'MediaDevices interface not available.' );
 }
```
###  使用tomcat ###
1.进入apache-tomcat-9.0.31\bin；双击启动startup.bat。

2.访问localhost:8080/three.js/Test1/demo1.html

