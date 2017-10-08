# git仓库点亮build图标

### 登录官网注册

* 使用github账号登录[官网](https://travis-ci.org/)
* 在右上角你的账户名点击进入 account，在Repositories tab页点击Sync now同步你的github项目

### 仓库配置



* 编写.travis.yml

  ```
  sudo: false
  language: node_js
  node_js:
    - '4'
    - '6'

  ```
* 编写执行脚本，以下为几种实现方式
  * package.json中自定main
  * script中指定test脚本
  * .travis.yml中指定script
  ```
  script:
  - npm run ci
  ```
