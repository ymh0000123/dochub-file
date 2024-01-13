# 原神好句API

## 通过JS调用

### html代码
```html
<div id="ys"></div>
```

::: tabs

@tab:active <Badge text="推荐" type="tip" /> 通过unpkg调用

### js代码

```js
//原神好句api by没用的小废鼠
fetch('https://unpkg.com/genshin-good-words/Good-words.txt')
.then(response => response.text())
.then(data => {
  const lines = data.split('\n');
  const randomLine = lines[Math.floor(Math.random() * lines.length)];
  document.getElementById('ys').innerText = randomLine;
})
.catch(error => {
  console.error('Error fetching ys:', error);
});
```


@tab 通过GIthub Pages调用

### js代码

```js
//原神好句api by没用的小废鼠
fetch('https://ymh0000123.github.io/Genshin-Good-words/Good-words.txt')
.then(response => response.text())
.then(data => {
  const lines = data.split('\n');
  const randomLine = lines[Math.floor(Math.random() * lines.length)];
  document.getElementById('ys').innerText = randomLine;
})
.catch(error => {
  console.error('Error fetching ys:', error);
});
```

@tab 通过jsdeliv调用

### js代码

```js
//原神好句api by没用的小废鼠
fetch('https://cdn.jsdelivr.net/gh/ymh0000123/Genshin-Good-words@master/Good-words.txt')
.then(response => response.text())
.then(data => {
  const lines = data.split('\n');
  const randomLine = lines[Math.floor(Math.random() * lines.length)];
  document.getElementById('ys').innerText = randomLine;
})
.catch(error => {
  console.error('Error fetching ys:', error);
});
```
:::

## cdn引入

### html代码
```html
<div id="ys"></div>
```

::: tabs

@tab:active 通过unpkg引入

```html
<script src="https://unpkg.com/genshin-good-words/script_npm.js"></script>
```
@tab 通过jsdelivr引入
```html
<script src="https://cdn.jsdelivr.net/gh/ymh0000123/Genshin-Good-words@main/script_jsdelivr.js"></script>
```
@tab 通过GIthub Pages引入
```html
<script src="https://ymh0000123.github.io/Genshin-Good-words/script.js"></script>
```
@tab 通过github.moeyy.xyz引入
```html
<script src="https://github.moeyy.xyz/https://raw.githubusercontent.com/ymh0000123/Genshin-Good-words/main/script.js"></script>
```
:::

## demo

<CodePen
  link="https://codepen.io/ymh0000123/pen/jOJPojy"
  title="原神好句API"
  status="clicktorun"
  :theme="$isDarkmode? 'dark': 'light'"
/>