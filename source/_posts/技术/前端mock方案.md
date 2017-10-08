# 前端mock方案

使用前后端分离模式进行开发，前端进行开发过程中，由于后端服务并没有写好或者已经写好但是服务不在本地环境，此时就需要mock数据来模拟数据请求。
常用的mock方案主要为两种：
* 通过本地json数据进行模拟
* 通过代理连接后台服务进行模拟

[示例代码](https://github.com/easy-templates/koa2-demo-mock)

## 本地数据模拟

* 根据接口文档，手工mock数据，此方式用起来最简单，只需要和后端约定之后自己按照规则创建json数据即可，缺点为无法生成大量的数据，没有随机性
* 根据接口文档，定义Mock数据的模板，使用生成Mock数据的工具(比如：faker.js、Mock.js)；优点是快速高效，修改起来方便

通过`koa2`的路由来实现请求对应的url时自动转为获取对应json文件并返回。

以下示例效果为请求/user时会返回user.json数据。

核心代码如下：

```
function mock() {
    mockList.forEach(function(config) {
        var url = config['url'];
        router[config['type']](url, async function(ctx, next) {
            var mockFile = require('../mockData/' + config['json']);
            ctx.body = JSON.stringify(mockFile);
            console.log('Mock URL: ', '\x1b[32m', config['url'] + ' --> ' + config['json'], '\x1b[0m', ' started.');
        });
    });
}
```
mockList格式如下：
```
module.exports = [
    // 获取人员信息
    {
      type: "get",
      url: "/user",
      json: "user.json"
    },
]

```
user.json文件存放在项目下的mockData目录下。


## 代理模拟

通过第三方库`koa-better-http-proxy`结合`koa2`来实现代理。此时请求url会自动从本地2000端口指向3201端口
核心代码如下：
```
proxyList.forEach(function(config) {
    app.use(proxy(config.host));
    console.log('Proxy :', '\x1b[33m', ' -> ', config.host, '\x1b[0m', ' Started.');
});
```
proxyList格式如下：
```
proxyList: [{
        host: 'http://127.0.0.1:3201',
    }], //代理服务器列表
```

