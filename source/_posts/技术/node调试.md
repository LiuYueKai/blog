1、  安装node-inspector

​     npm install -g node-inspector

2、编写app.js起web服务

3、起调试监听

​     node-inspector

注：会占用8080端口，修改端口可以通过 node-inspector --web-port 3456

4、通过debug调用app

​     node --debug app.js

​     node --debug-brk=5858 gulp.js //此种方式浏览器加载之后会停留在第一行，上面的方式不会停留

5、打开chrome地址稍等片刻

​     http://127.0.0.1:8080/?port=5858

注：5858端口也被占用了。