# window下可用文件在linux下不可用 

## 描述：
#!/bin/bash/env node 执行提示没有那个文件或目录

## 原因：
window下创建的文件 \r字符会被显示为^M，导致识别错误

## 解决方案：
执行下面的命令

    sed -i 's/\r$//' fileName
    
整句意思是把以\r结束的字符换成空白    
    
* -i 插入

* s替代模式

* \r$表示任何以\r结束的字符

参考页面：

http://www.2cto.com/os/201310/252970.html

## macos需特殊处理


http://www.netingcn.com/mac-osx-sed-command-expects-followed-by-text.html

网上方法未实现，通过重新创建文件的方式来实现了
