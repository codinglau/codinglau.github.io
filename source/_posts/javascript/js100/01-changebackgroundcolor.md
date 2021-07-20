---
title: JS100-01 Change Background Color
date: 2021-07-18 19:16:49
cover: https://i.imgur.com/M6DvDUn.gif
categories:
- Web Development
- JavaScript
tags:
- JavaScript
- JS100 Challenge
toc: true
---

1st Challenge: To randomly change a website's background color upon a button click

<a href="https://codinglau.github.io/js100/01-changebgcolor" target="_blank">
    <button class="button is-danger is-rounded is-medium">
        <span class="icon">
        <i class="fab fa-github"></i>
        </span>
        <span>Demo</span>
    </button>
</a>

<!-- more -->

# Keys to complete this challenge

* How could we generate random colors?
    - [X] [Math.floor()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/floor)
    - [X] [Math.random()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random)
    - [X] [rgb()](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/rgb())

# Possible Steps

## 1. Add a button to the HTML document

{% codeblock HTML Document lang:html %}
<body>
    <button>click me</button>
</body>
{% endcodeblock %}

## 2. Write a JavaScript function that would return a random color e.g. `rgb(10, 20, 30)`

{% codeblock Function getRandomColor() lang:html %}
<script>
    // function that returns a random rgb color
    // e.g. rgb(10, 20, 30)
    function randomRgbColor(){
        const r = Math.floor(Math.random() * 256);
        const g = Math.floor(Math.random() * 256);
        const b = Math.floor(Math.random() * 256);
        return `rgb(${r}, ${g}, ${b})`;
    }
</script>
{% endcodeblock %}

> The `Math.random()` function returns a floating-point, pseudo-random number in the range 0 to less than 1 (inclusive of 0, but not 1) with approximately uniform distribution over that range.

> `Math.random() * 256` would return a random floating number ranges from 0 to 256 (inclusive of 0, but not 256).

> `Math.floor(floating-number)` would return the largest integer that is smaller than the `floating-number`.

> Therefore, `Math.floor(Math.random() * 256)` is going to return a random `integer` ranges from 0 to 255.


## 3. Select the button using JavaScript
## 4. Listen to the `click` event of the selected button
## 5. When the button is being clicked, set `<body>`'s background color

{% codeblock lang:javascript %}
const btn = document.querySelector('button');   // select the button

// listen to click event of the button
btn.addEventListener('click', function(){
    document.body.style.backgroundColor = randomRgbColor();
})
{% endcodeblock %}

# Complete Source Code

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

<!-- <script>
    function onTabClick(e) {
        if (!$(e.currentTarget).hasClass('is-active')) {
            $('.is-active').toggleClass('is-active');
            $(e.currentTarget).toggleClass('is-active');
            $('.tab-content.is-block').toggleClass(['is-block', 'is-hidden']);
            let tabId = $(e.currentTarget).attr("data-id");
            $(tabId).toggleClass(['is-block', 'is-hidden']);
        }
    }
</script> -->