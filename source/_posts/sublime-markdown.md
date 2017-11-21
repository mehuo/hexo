---
 layout: post
 title: "sublime安装markdown插件"
 date: 2017-10-17
 comments: true
 tags: 
    - sublime
    - markdown
---

# sublime编辑器安装markdown插件
## 第一步 安装
在sublime中使用快捷键 Ctrl+shift+p 调出输入框，然后输入pcip
![image](/images/hexo/tools/sm-1.png)
然后选择 markdown preview点击。
或者直接点击 Preferences --> 选择 Package Control: ，然后输入install也可以安装

## 第二步，设置直接在浏览器中预览的快捷键(可省略)
点击 Preferences --> 选择 Key Bindings User，输入：
{ "keys": ["alt+m"], "command": "markdown_preview", "args": {"target": "browser", "parser":"markdown"} }
保存后，直接输入快捷键：Alt + M 就可以直接在浏览器中预览生成的HTML文件了。

## 第三步 设置markdown高亮
Ctrl+shift+p 找到下图中的设置语法的选项，点击即可设置成功
![image](/images/hexo/tools/sm-2.png)

## 其他功能
输入Ctrl+shift+p 调出输入框后输入markdown看到的都是可以操作的
![image](/images/hexo/tools/sm-3.png)
如果执行save to html的话，就会在此文件同级目录下生成一个html文件









