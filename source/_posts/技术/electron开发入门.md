# electron

Build cross platform desktop apps with JavaScript, HTML, and CSS



# 核心概念

## main process

主进程，通常是指 `main.js` 文件，是每个 Electron 应用的入口文件。它控制着整个 APP 的生命周期，从打开到关闭。它也管理着原生元素比如菜单，菜单栏，Dock 栏，托盘等。主进程负责创建 APP 的每个渲染进程。而且整个 Node API 都集成在里面。

每个 app 的主进程文件都定义在 `package.json` 中的 `main` 属性当中，这也是为什么 `electron .` 能够知道应该使用哪个文件来启动。


## renderer process

渲染进程是你的应用内的一个浏览器窗口。与主进程不同的是，它能够同时存在多个而且运行在不一样的进程。而且它们也能够被隐藏。

在通常的浏览器内，网页通常运行在一个沙盒的环境挡住并且不能够使用原生的资源。然而 Electron 的用户在 Node.js 的 API 支持下可以在页面中和操作系统进行一些低级别的交互。

## IPC

IPC 代表 Inter-Process Communication。Electron 使用 IPC 来在 [主进程] 和 [渲染进程] 之间传递 JSON 信息。

## 其他术语

[参照文档](https://github.com/electron/electron/blob/master/docs-translations/zh-CN/glossary.md)
# quick start

```bash
# Clone this repository
git clone https://github.com/electron/electron-quick-start
# Go into the repository
cd electron-quick-start
# Install dependencies
npm install
# Run the app
npm start
```
# 核心代码说明

## 入口
`package.json` 中的 `main` 属性

## main.js

* 通过[BrowserWindow](https://github.com/electron/electron/blob/master/docs-translations/zh-CN/api/browser-window.md)对象来创建和控制浏览器窗口
* [app](https://github.com/electron/electron/blob/master/docs-translations/zh-CN/api/app.md)模块是为了控制整个应用的生命周期设计的
* 文件改变之后自动加载:
```
require('electron-reload')(__dirname, {
    electron: path.join(__dirname, 'node_modules', '.bin', 'electron')
});
```
缺陷：如果是主进程改变并不会重启服务，只是重新打开窗口，因此目前相当于仅监听了渲染进程以及html的改变。
* ​加载主进程
```
function loadMainProcess() {
    var files = glob.sync(path.join(__dirname, 'main-process/**/*.js'))
    files.forEach(function(file) {
        require(file)
    })
}
```
## 进程通信
### 渲染进程
```
const ipc = require('electron').ipcRenderer

const asyncMsgBtn = document.getElementById('async-msg')

asyncMsgBtn.addEventListener('click', function () {
  ipc.send('asynchronous-message', 'ping')
})

ipc.on('asynchronous-reply', function (event, arg) {
  const message = `异步消息回复: ${arg}`
  document.getElementById('async-reply').innerHTML = message
})
```

### 主进程
```
const ipc = require('electron').ipcMain

ipc.on('asynchronous-message', function (event, arg) {
  event.sender.send('asynchronous-reply', 'pong')
})
```
### 文档说明：
[ipcMain](https://github.com/electron/electron/blob/master/docs-translations/zh-CN/api/ipc-main.md)
[ipcRenderer](https://github.com/electron/electron/blob/master/docs-translations/zh-CN/api/ipc-renderer.md)

## 引入第三方资源
在渲染进程中添加如下代码：
```
const $ = require('jquery');
jQuery = $;
const ztree = require('ztree');
```
在html中添加如下代码：
```
<link rel="stylesheet" href="node_modules\ztree\css\zTreeStyle\zTreeStyle.css">
```
注：网上存在另外一种方式在html中引入第三方js资源，本文档中不进行介绍，请自行搜索

## 调试
* 渲染进程调试：
  在main.js中创建了BrowserWindow之后添加如下代码：
```
if (debug) {
   mainWindow.webContents.openDevTools()
   mainWindow.maximize()
}
```
* 主进程调试：

  [参照文档](https://github.com/electron/electron/blob/master/docs-translations/zh-CN/tutorial/debugging-main-process.md)
# 参考文档


[中文文档](https://github.com/electron/electron/tree/master/docs-translations/zh-CN)
[API demos]可直接在官网首页下载，也可以下载[中文工程](https://github.com/demopark/electron-api-demos-Zh_CN)后本地启动