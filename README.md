<!-- TOC -->

- [1. 目录](#1-目录)
    - [1.1. 前端](#11-前端)
        - [1.1.1. [vue-element-admin使用](https://github.com/kelvinliu11/blogs/blob/master/前端/vue-element-admin使用.md)](#111-vue-element-admin使用httpsgithubcomkelvinliu11blogsblobmaster前端vue-element-admin使用md)
        - [1.1.2. [常用工具&命令](https://github.com/kelvinliu11/blogs/blob/master/常用工具与命令.md)](#112-常用工具命令httpsgithubcomkelvinliu11blogsblobmaster常用工具与命令md)
        - [1.1.3. [数仓BI](https://github.com/kelvinliu11/blogs/blob/master/数仓BI/数仓BI.md)](#113-数仓bihttpsgithubcomkelvinliu11blogsblobmaster数仓bi数仓bimd)
- [2. 工具](#2-工具)
    - [2.1. 使用vscode、Markdown Preview Enhanced、Paste Image](#21-使用vscodemarkdown-preview-enhancedpaste-image)
        - [2.1.1. Paste Image插件配置](#211-paste-image插件配置)
        - [2.1.2. Paste Image使用ctrl + alt + v，可以将粘贴板中的文件直接放到img目录下，并在文档中引用](#212-paste-image使用ctrl--alt--v可以将粘贴板中的文件直接放到img目录下并在文档中引用)
        - [2.1.3. markdown toc](#213-markdown-toc)
        - [2.1.4. markdown中，加粗的字没有换行，需要在加粗文字之后加两个空格](#214-markdown中加粗的字没有换行需要在加粗文字之后加两个空格)
        - [2.1.5. 多级列表](#215-多级列表)
        - [2.1.6. 在vscode中批量替换换行](#216-在vscode中批量替换换行)
    - [2.2. github项目clone（使用vscode）](#22-github项目clone使用vscode)
    - [2.3. markdown表格工具http://www.tablesgenerator.com/markdown_tables](#23-markdown表格工具httpwwwtablesgeneratorcommarkdown_tables)
    - [2.4. url文章转markdown](#24-url文章转markdown)

<!-- /TOC -->
# 1. 目录
## 1.1. 前端
### 1.1.1. [vue-element-admin使用](https://github.com/kelvinliu11/blogs/blob/master/前端/vue-element-admin使用.md)
### 1.1.2. [常用工具&命令](https://github.com/kelvinliu11/blogs/blob/master/常用工具与命令.md)
### 1.1.3. [数仓BI](https://github.com/kelvinliu11/blogs/blob/master/数仓BI/数仓BI.md)

# 2. 工具
## 2.1. 使用vscode、Markdown Preview Enhanced、Paste Image
下载vscode之后，安装抄件Markdown Preview Enhanced、Paste Image
### 2.1.1. Paste Image插件配置
在此插件的Path配置项后面加img目录，目的是保证保存的文件会放到一个统一的img目录下
![](img/2019-09-19-11-36-26.png)
### 2.1.2. Paste Image使用ctrl + alt + v，可以将粘贴板中的文件直接放到img目录下，并在文档中引用
### 2.1.3. markdown toc
插件如下图安装  
![](img/2019-09-19-15-25-34.png)  
可能会样式错乱，是因为换行符号不对，进行如下调整  
![](img/2019-09-19-15-32-12.png)
右键，先插入或更新编号，再插入toc，最终结果如下  
![](img/2019-09-19-15-34-27.png)
![](img/2019-09-19-15-33-58.png)
### 2.1.4. markdown中，加粗的字没有换行，需要在加粗文字之后加两个空格
### 2.1.5. 多级列表
可以使用+ - * 来做编排，然后下一级的文档，需要用tab键，然后跟上 + - * 然后空格后是正文，才能体现出来
### 2.1.6. 在vscode中批量替换换行
^\s*(?=\r?$)\n

## 2.2. github项目clone（使用vscode）
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

## 2.3. markdown表格工具http://www.tablesgenerator.com/markdown_tables#
因为在markdown中制作手写表格代码较多，用上面的工具生成，正向逆向都OK
![](img/2019-09-19-13-38-22.png)

## 2.4. url文章转markdown
https://markdown.readmorejoy.com/?ref=appinn