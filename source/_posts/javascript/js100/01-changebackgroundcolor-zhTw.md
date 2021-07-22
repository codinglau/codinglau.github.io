---
title: JS100 第一關 - 隨機轉換網頁背景顏色
date: 2021-07-19 23:55:40
lang: zh-tw
cover: https://i.imgur.com/M6DvDUn.gif
categories:
- Web Development
- JavaScript
tags:
- 中文
- JavaScript
- JS100 Challenge
toc: true
---

<a href="https://codinglau.github.io/js100/01-change-bgcolor" target="_blank">
    <button class="button is-success is-rounded is-medium">
        <span class="icon">
        <i class="fab fa-github"></i>
        </span>
        <span>Demo</span>
    </button>
</a>

<!-- more -->

# 過關重點

* 怎樣才能產生隨機顏色？
    - [X] [Math.floor()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/floor)
    - [X] [Math.random()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random)
    - [X] [rgb()](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/rgb())

# 步驟

## 1. 在 HTML 文件裡加入按鈕

{% codeblock HTML 文件 lang:html %}
<body>
    <button>click me</button>
</body>
{% endcodeblock %}

## 2. 建立可以隨機產生產顏色的函數

例如：呼叫函數時會返回`rgb(10, 20, 30)`

{% codeblock 函數 getRandomColor() lang:html %}
<script>
    // 呼叫函數時會返回`rgb(10, 20, 30)`
    function randomRgbColor(){
        const r = Math.floor(Math.random() * 256);
        const g = Math.floor(Math.random() * 256);
        const b = Math.floor(Math.random() * 256);
        return `rgb(${r}, ${g}, ${b})`;
    }
</script>
{% endcodeblock %}
> `Math.random()` 會返回 0 到 1 之間的隨機小數，包括 0，但不包括 1。

> 因此，`Math.random() * 256` 會返回 0 到 256 之間的隨機數 （帶小數點）。

> 然後利用 `Math.floor()` 把使用 `Math.random() * 256` 返回的隨機數變為整數。例如，`Math.random() * 256` 返回 99.8，`Math.floor(Math.random() * 256)` 會將 99.8 變成 99。 

> 這樣 `Math.floor(Math.random() * 256)` 就會返回 0 到 255 的隨機`整數`。剛好是rgb(r, g, b)裡所需要的數字。


## 3. 利用 JavaScript 選取按鈕
## 4. 監聽按鈕被按 `click` 的事件 
## 5. 當按下按鈕時，把網頁的背景顏色設為等於 `getRandomColor()` 函數返回的隨機顏色

{% codeblock lang:javascript %}
const btn = document.querySelector("button");

btn.addEventListener('click', function(){
    document.body.style.backgroundColor = randomRgbColor();
})
{% endcodeblock %}

# 完整程式碼

{% codeblock index.html lang:html %}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="./style.css">
    <title>JS100 Challenge 01 - Change Background Color</title>
</head>
<body>
    <button>click me</button>

    <script src="./app.js"></script>
</body>
</html>
{% endcodeblock %}

{% codeblock style.css lang:css %}
body {
    padding: 0;
    margin: 0;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
}

button {
    cursor: pointer;
    background-color: #000;
    color: #fff;
    padding: .5rem;
    border: 1px solid #fff;
    border-radius: .5rem;
}

button:hover {
    background-color: #fa0;
}
{% endcodeblock %}

{% codeblock app.js lang:javascript %}
const btn = document.querySelector('button');   // select the button

// listen to click event of the button
btn.addEventListener('click', function(){
    document.body.style.backgroundColor = randomRgbColor();
})

// function that returns a random rgb color
function randomRgbColor(){
    const r = Math.floor(Math.random() * 256);
    const g = Math.floor(Math.random() * 256);
    const b = Math.floor(Math.random() * 256);
    return `rgb(${r}, ${g}, ${b})`;
}
{% endcodeblock %}