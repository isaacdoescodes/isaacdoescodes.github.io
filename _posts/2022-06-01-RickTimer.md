---
title: Making The Rick Timer
layout: post
tags: projects
---
The #1 best way to rickroll someone

So I was wondering what the best way to rickroll someone would be. I decided it would be to make a timer and launch a rickroll once its done. So I searched the internet to find what I was looking for but it didn't exist, so I made it.

<a href="https://www.isaacdoescodes.com/ricktimer">Check it out here</a>

<iframe src="https://ghbtns.com/github-btn.html?user=isaacdoescodes&repo=ricktimer&type=star&size=large" frameborder="0" scrolling="0" width="170" height="30" title="GitHub"></iframe>

Before we get into the code I just want to quickly explain what the Rick Timer is. Essentially, it is given a time and then the window will unminimize itself and open a new tab with a rickroll in it.



## How I made it.

I started by creating a boilerplate html page
```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rick Timer</title>
</head>
<body>
    
</body>
</html>
```
and adding some markup
```html
    <div class="manual" id="manual">
        <h1>Rick Timer</h1>
        <h4>Will launch a rickroll after a specified time, even when window is minimized. Usefull for pranking someone.
        </h4>
        <h3>
            NOTE: You MUST enable popups. If on chrome go to the padlock then [site settings] then find popups and change[blocked] to [allow]
        </h3>

        Timer length: <input id="time" placeholder="60" />seconds
        <br><br>
        <button onclick="starttimer(document.getElementById('time').value);">Start RickTimer</button><br>
        This was made IsaacDoesCodes. It would make him very gratefull if you <a
            href="https://www.tiktok.com/@isaacdoescodes">followed him on tiktok</a>
        <h3>After starting timer <i>MINIMIZE</i> the window</h3>
    </div>
```
![](/assets/img/ricktimernocss.png){: width='700'}

not looking too good lets add some css

```css
body {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

.manual {
    width: 100%;
    max-width: 75ch;
    margin: auto;
}

#time {
    text-align: right;
    padding: 10px;
    width: 50px;
}

button {
    padding: 10px;
}
```

![](/assets/img/ricktimercss.png){: width='700'}

thats better. Now lets do the important stuff, the javascript.

```javascript
// Function called by button 'secs' is the property passed by the button which grabs the value from the text box.
function starttimer(secs) { 
    if (secs == "") {
        secs = 60; // If no value default to one minute.
    }
    document.title = "New Tab"; // Sets tab text to new tab
    document.getElementById("manual").style.display = "none"; // Hides content
    window.setTimeout(() => {
        window.open("https://www.youtube.com/watch?v=a3Z7zEc7AXQ"); // Open Rickroll video
    }, (secs) * 1000) // Inputed time minus half a second, converted to miliseconds.
}
```

What this does is sets a 'timeout' that after the entered time (converted to ms) will open a new tab with a rickroll in it. Conveniently, when the browser opens a new tab it unminimizes itself on macos and windows so thats handy.


There is only one caveat to this though and thats popup windows need to be enabled. There is a simple fix to make sure they are enabled and thats have a loading screen that says 'If nothing happens, please enable popup windows.' and than open the actual page but I won't include that here.