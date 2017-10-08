## 具体实现demo

https://github.com/LiuYueKai/atom-easy-server

## 文件说明

### keymaps
记录快捷键设置


```
{
  "atom-workspace": {
    "ctrl-alt-o": "first-for-atom:toggle"
  }
}

```

### menus
记录toolBar以及右键设置

* context-menu：编辑器内部右键menu
* menu：toolBar对应的menu

    
```
{
  "context-menu": {
    "atom-text-editor": [
      {
        "label": "Toggle first-for-atom",
        "command": "first-for-atom:toggle"
      }
    ]
  },
  "menu": [
    {
      "label": "Packages",
      "submenu": [
        {
          "label": "first-for-atom",
          "submenu": [
            {
              "label": "Toggle",
              "command": "first-for-atom:toggle"
            }
          ]
        }
      ]
    }
  ]
}

```


### package核心参数

* main：入口文件
* activationCommands：一个对象， 说明哪个命令来激活你的插件。如果不填写, 则Atom会在插件激活时，自动调用 activate()函数。