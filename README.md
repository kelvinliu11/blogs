[toc]
<!-- TOC -->autoauto- [目录](#目录)auto    - [前端](#前端)auto        - [一、[vue-element-admin使用](https://github.com/kelvinliu11/blogs/blob/master/前端/vue-element-admin使用.md)](#一vue-element-admin使用httpsgithubcomkelvinliu11blogsblobmastervue-element-admin使用md)auto- [工具](#工具)auto    - [使用vscode、Markdown Preview Enhanced、Paste Image](#使用vscodemarkdown-preview-enhancedpaste-image)auto        - [Paste Image插件配置](#paste-image插件配置)auto        - [Paste Image使用ctrl + alt + v，可以将粘贴板中的文件直接放到img目录下，并在文档中引用](#paste-image使用ctrl--alt--v可以将粘贴板中的文件直接放到img目录下并在文档中引用)auto        - [markdown toc](#markdown-toc)auto    - [github项目clone（使用vscode）](#github项目clone使用vscode)auto    - [三、markdown表格工具http://www.tablesgenerator.com/markdown_tables](#三markdown表格工具httpwwwtablesgeneratorcommarkdown_tables)autoauto<!-- /TOC -->
# 目录
## 前端
### 一、[vue-element-admin使用](https://github.com/kelvinliu11/blogs/blob/master/%E5%89%8D%E7%AB%AF/vue-element-admin使用.md)


# 工具
## 使用vscode、Markdown Preview Enhanced、Paste Image
下载vscode之后，安装抄件Markdown Preview Enhanced、Paste Image
### Paste Image插件配置
在此插件的Path配置项后面加img目录，目的是保证保存的文件会放到一个统一的img目录下
![](img/2019-09-19-11-36-26.png)
### Paste Image使用ctrl + alt + v，可以将粘贴板中的文件直接放到img目录下，并在文档中引用
### markdown toc
![](img/2019-09-19-15-25-34.png)

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