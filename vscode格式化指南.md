### 安装vetur插件
```
配置文件添加一下代码
"vetur.format.defaultFormatter.html": "js-beautify-html",// #vue组件中html代码格式化样式
"vetur.format.defaultFormatterOptions": {
    "js-beautify-html": {
      "wrap_attributes": "auto",
      "wrap_line_length": 150   //html标签的长度
    }
  },
```
