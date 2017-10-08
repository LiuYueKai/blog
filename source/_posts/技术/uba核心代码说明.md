# uba核心代码说明

## 默认命令

```
uba -v
uba -h
```
* 执行默认命令首先判断 /.uba/uba-plugin.json是否存在，如果不存在则创建
  * mac为当前用户根目录下 `/Users/liuyk`
  * ​
* 更新/.uba/uba-plugin.json下插件：`["install", "init", "plugin", "server","build"]`的版本信息
  **此部分会有问题，第三方的没有处理。**

## 执行第三方插件

```
uba init
```
* 首先去uba的安装目录的node_modules下判断是否存在第三方插件库，如果不存在则提示安装
* 通过require(`uba-${commands[0]}`).plugin来调用第三方库，默认参数为
```
var opts = {
  cmd: commands,
  argv: argv,
  name: require("../package.json").name
};

var pluginPath = findPluginPath(commands[0]);
if (pluginPath) {
  if (require(`uba-${commands[0]}`).plugin) {
    require(`uba-${commands[0]}`).plugin(opts);
  } else {
    console.log(chalk.red("  Error : Plugin internal error."));
  }
}
```

## 第三方插件规范

* 模块的exports中包含plugin作为入口方法，并且接受默认参数(参照上面的说明)

## 第三方插件安装

```
uba install sa
```
* 首先安装uba-sa仓库至uba的安装目录
* 更新`/.uba/uba-plugin.json`中关于此插件的版本信息