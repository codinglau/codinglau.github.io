---
title: JS100-01 Change Background Color
date: 2021-07-18 19:16:49
categories:
- Web Development
- JavaScript
tags:
- JavaScript
- JS100 Challenge
toc: true
---

JS100-01 轉換背景顏色

<!-- more -->

<div class="tabs is-centered is-boxed">
    <ul style="margin: 0">
        <li class="is-active" onclick="onTabClick(event)" data-id="#english">
            <a>
                <span class="icon is-small"><i class="fas fa-globe-americas" aria-hidden="true"></i></span>
                <span>English</span>
            </a>
        </li>
        <li onclick="onTabClick(event)" data-id="#chinese">
            <a>
                <span class="icon is-small"><i class="fas fa-globe-asia" aria-hidden="true"></i></span>
                <span>中文</span>
            </a>
        </li>
    </ul>
</div>


<div id="english" class="tab-content is-block">

# Keys to complete this challenge

* How could we generate random colors?
    - [X] [Math.floor()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/floor)
    - [X] [Math.random()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random)
    - [X] [rgb()](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/rgb())

## Possible Steps
1. Add a button to the HTML document
2. Write a function that would return a random color e.g. `rgb(10, 20, 30)` each time when we call it
3. Select the button using JavaScript
4. Listen to the `click` event of the selected button
5. When the button is being clicked, set `<body>`'s background color to the function created in `step 2`

### S1. Add a button to the HTML document
{% codeblock HTML Document lang:html %}
<body>
    <button>click me</button>
</body>
{% endcodeblock %}

### S2. Write a function that would return a random color
{% codeblock Function getRandomColor() lang:html %}
<script>
    // function that returns a random rgb color
    // e.g. rgb(10, 20, 30)
    function getRandomColor(){
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

### S3-5. Select button, listen to click event, change body's background color
{% codeblock lang:javascript %}
const btn = document.querySelector("button");

// listen to click event of the button
btn.addEventListener('click', function(){
    document.body.style.backgroundColor = getRandomColor();
})
{% endcodeblock %}

## Full code
> Don't worry about the CSS code below. We will discuss CSS in another section.
{% codeblock Select the button lang:html %}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS100 Challenge 01 - Change Background Color</title>
    <style>
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
    </style>
</head>
<body>
    <button>click me</button>

    <script>
        const btn = document.querySelector("button");   // select the button

        // listen to click event of the button
        btn.addEventListener('click', function(){
            document.body.style.backgroundColor = getRandomColor();
        })

        // function that returns a random rgb color
        function getRandomColor(){
            const r = Math.floor(Math.random() * 256);
            const g = Math.floor(Math.random() * 256);
            const b = Math.floor(Math.random() * 256);
            return `rgb(${r}, ${g}, ${b})`;
        }
    </script>
</body>
</html>
{% endcodeblock %}

</div>

<div id="chinese" class="tab-content is-hidden">
    [网易云音乐](https://music.163.com/) 是一款专注于发现与分享的音乐产品,依托专业音乐人、DJ、好友推荐及社交功能,为用户打造全新的音乐生活。
</div>

<script>
    function onTabClick(e) {
        if (!$(e.currentTarget).hasClass('is-active')) {
            $('.is-active').toggleClass('is-active');
            $(e.currentTarget).toggleClass('is-active');
            $('.tab-content.is-block').toggleClass(['is-block', 'is-hidden']);
            let tabId = $(e.currentTarget).attr("data-id");
            $(tabId).toggleClass(['is-block', 'is-hidden']);
        }
    }
</script>