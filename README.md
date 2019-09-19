[toc]
# 目录
## 前端
+ vue-element-admin使用
# 工具
## 使用vscode、Markdown Preview Enhanced、Paste Image
下载vscode之后，安装抄件Markdown Preview Enhanced、Paste Image
### Paste Image插件配置
在此插件的Path配置项后面加img目录，目的是保证保存的文件会放到一个统一的img目录下
![](img/2019-09-19-11-36-26.png)
### Paste Image使用ctrl + alt + v，可以将粘贴板中的文件直接放到img目录下，并在文档中引用

## github项目clone（使用vscode）
+ vscode中 Terminal -> New Terminal
+ 执行以下命令clone
```
echo "# blogs" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/xxx/blogs.git   这里是你的github项目仓库地址
git push -u origin master
```

## 三、markdown表格工具http://www.tablesgenerator.com/markdown_tables#
因为在markdown中制作手写表格代码较多，用上面的工具生成，正向逆向都OK
![](img/2019-09-19-13-38-22.png)