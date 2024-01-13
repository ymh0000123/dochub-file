# 使用GitHub Pages免费搭建自己的网站

## 视频教程
<BiliBili bvid="BV1hC4y1n7oQ" />

## 准备工作
 1. 一个GitHub账号

## 创建仓库

点击 [这里](https://github.com/new) 跳转到创建仓库界面

仓库名称为 `<username>.github.io`并且设置为公开仓库

> 注意：`<username>` 替换为你的GitHub用户名，只有把你的仓库命名为`<username>.github.io` 才能得到`<username>`.github.io 这个域名

## 创建网站

创建一个名称为 `index.html`的文件放在根目录下

> 注意：`index.html` 文件名不能修改，否则无法访问

如果你不会html可以到 [HTML 教程](https://www.runoob.com/html/html-tutorial.html) 学习

下面是一个例子

```html
<!DOCTYPE html>
<html>
<body>
<h1>Hello World</h1>
<p>这是一个使用 GitHub Pages的网站</p>
</body>
</html>
```

## 配置GitHub Pages

点击 设置 > Pages 

找到构建和部署，点击`None`选择你放文件的分支然后选择 `/(root)` 点击Save 等待1分钟刷新网页就可以看到网站的域名了