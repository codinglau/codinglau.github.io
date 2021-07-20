---
title: JS100-02 Hex Change Background Color
date: 2021-07-20 21:49:01
cover: https://i.imgur.com/fzSBvbT.gif
categories:
- Web Development
- JavaScript
tags:
- JavaScript
- JS100 Challenge
toc: true
---

2nd Challenge: To randomly change a website's background color upon a button click

<a href="https://codinglau.github.io/js100/02-hexchangebgcolor" target="_blank">
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
    - [X] [Number.prototype.toString()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toString)

# Possible Steps

## 1. Add a button to the HTML document

{% codeblock HTML Document lang:html %}
<body>
    <!-- we are going to insert hex color code into <p></p> using JavaScript-->
    <p></p>
    <button>click me</button>
</body>
{% endcodeblock %}

## 2. Write a JavaScript function that would return a base-16 number
{% codeblock Function getRandomColor() lang:html %}
<script>
    function numToHex() {
        return (Math.floor(Math.random() * 15) + 1).toString(16).toUpperCase();
    }
</script>
{% endcodeblock %}

<article class="message is-success">
    <div class="message-header">
        <p>Notes</p>
        <button class="delete" aria-label="delete"></button>
    </div>
    <div class="message-body">
        <p>Hex color code is  a combination of 0, 1,...E, F. e.g. #A1B2C3.</p>
        <p>When we convert 1, 2,...,15(base 10) to base 16, we are going to get 0, 1,...,F.</p>
        <p>Number.toString() could help us transform a base-10 number to a base-16 number. e.g. (10).toString() </p>
    </div>
</article>

## 3. Write a JavaScript to form the hex color code

{% codeblock Function getRandomColor() lang:html %}
<script>
    // function that returns a random hex color
    function randomHexColor(){
        let hexCode = '#';
        while(hexCode.length < 7) {
            hexCode += numToHex();
        }
        return hexCode;
    }
</script>
{% endcodeblock %}

## 4. Select the button using JavaScript
## 5. Listen to the `click` event of the selected button
## 6. When the button is being clicked, set `<body>`'s background color

{% codeblock Function getRandomColor() lang:html %}
<script>
    // listen to click event of the button
    btn.addEventListener('click', function(){
        let hexColor = randomHexColor();
        document.body.style.backgroundColor = hexColor;
        p.textContent = `Hex Color: ${hexColor}`
    })
</script>
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
    <title>JS100 Challenge 02 - Hex Change Background Color</title>
</head>
<body>
    <p></p>
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
    flex-direction: column;
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
const p = document.querySelector('p');

// listen to click event of the button
btn.addEventListener('click', function(){
    let hexColor = randomHexColor();
    document.body.style.backgroundColor = hexColor;
    p.textContent = `Hex Color: ${hexColor}`
})

function numToHex() {
    return (Math.floor(Math.random() * 15) + 1).toString(16).toUpperCase();
}

// function that returns a random rgb color
function randomHexColor(){
    let hexCode = '#';
    while(hexCode.length < 7) {
        hexCode += numToHex();
    }
    return hexCode;
}
{% endcodeblock %}