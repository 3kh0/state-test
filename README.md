# State Testing Unrestricted
**Ways to take state tests unrestricted.**

We are trying to get almost every state, if you have a different state, open a issue with the title of your state and provide AS MUCH DETAIL AS POSSIBLE about how you take your state tests.

- [State Testing Unrestricted](#state-testing-unrestricted)
  * [North Carolina](#north-carolina)
    + [The easy method](#the-easy-method)
    + [The hard method](#the-hard-method)
  * [Wisconsin](#wisconsin)
    + [Forward Exam](#forward-exam)
    + [STAR test](#star-test)
  * [California](#california)
    + [CAASPP](#caaspp)

<small><i><a href='http://github.com/3kh0/readme-toc/'>Table of contents generated with readme-toc</a></i></small>

## North Carolina
~~This is the first one bc I live in that state lol~~

The first thing you need to know is the way that the NCTest app was made was really stupid, it pretty much just iframes a existing page that you can search on google

![Screenshot 2023-05-09 09 09 05](https://github.com/3kh0/state-test/assets/58097612/010fe95c-5fdf-4d24-86ec-55592810fe9e)

The link there in question is [data.ncsu.edu/nctest/Destination.html](https://data.ncsu.edu/nctest/Destination.html), but if you click on the NCTest login, you would be blocked from logging in with this message.

![Screenshot 2023-05-09 09 12 59](https://github.com/3kh0/state-test/assets/58097612/dd341dc1-1d2d-4ab4-bbd1-f216d3858f8a)

Thank goodness the devs behind it for some reason added comments to their code, so we can exploit this. This function checks the user agent and deterimes if the test taker is in a "secure" testing environment. This only checks the first 6 characters of the user agent and if it is `NCTest`. Note this is a very simple way of how it works, so here are two ways to bypass and get this running.

```js
//check useragent for our custom chrome app string
function onMessage(e) {

    appWindow = e.source;
    appOrigin = e.origin;
    oldAgent = navigator.userAgent;

    //customizing useragent due to sporadic issue of not being overwritten in chrome app
    if ( navigator.userAgent.substring(0, 6) !== "NCTest" ) {
        Object.defineProperty(navigator, 'userAgent', {
            get: function () { return "NCTest/1.0 ChromeApp " + oldAgent; }
        });
    }
    isChromeApp=true;
}
```
*Source: [data.ncsu.edu/nctest/common.js](https://data.ncsu.edu/nctest/common.js) Archived: [pastebin.com/gVAUnkwW](https://pastebin.com/gVAUnkwW)*

### The easy method

This is a much easy way without having to spoof useragents, this also depends if you can install the app on your device, this can work on Windows and Linux, but sometimes it does break, relaunching does seem to fix the issue of getting blocked.

1. Get the [NCTest App](https://chrome.google.com/webstore/detail/nctest/gekbonallhcfalincpgmjcipmjehfhlh/) from the Chrome Web Store
2. This step depends on your OS,

**If you are on a Chromebook**
1. Open the Launcher ![Screenshot 2023-05-09 09 29 18](https://github.com/3kh0/state-test/assets/58097612/31a98908-a306-474e-99b1-5ebf2d2d7bbd)
2. Locate the NCTest App and click on it
![Screenshot 2023-05-09 09 29 38](https://github.com/3kh0/state-test/assets/58097612/493073f5-373d-4a8e-854f-6efe8f056add)
3. Click the NCTest login (or whatever you need the app for)
4. Profit

**If you are on Linux/Windows**
1. Go to `chrome://apps`
2. Click on the NCTest App
3. Click the NCTest login (or whatever you need the app for)

> **Note**
> If it still shows the block scren, close the app and reopen it.

In this app, you can use keybinds suck as `alt`+`tab` to change windows while taking the test. I did not figure out how to resize the window, it seems it is locked to fill the screen.

![Screenshot 2023-05-09 09 24 52](https://github.com/3kh0/state-test/assets/58097612/6709e882-dba4-4924-ac34-8f3e57fd2737)

### The hard method

Coming soon, still researching on how this works and the best way to do it.

Further Reading:
- https://defcon.social/@3kh0/110293819888798643

## Wisconsin

Here is how to bypass the exams for wisconsin.

### Forward Exam

Forward Exams are provided through DRC Insight, which can be accessed [here](https://wbte.drcedirect.com/WI/portals/wi). However, it hides the test sign-in option if the client is not in the designated kiosk. However, this is done on the client-side, and as any developer knows, you should never trust the client side. Looking through the code, the following line immediately jumps out:

```html
<a href="/WI/?adminId=553270&amp;index=1#portal/wi/553270/exam" id="testLink1" index="1" class="hide-link">Test Sign In</a>
```

Right there, see it? `class="hide-link"`. I threw together a little script to remove the class, and it ended up looking like this:

```js
var a = document.getElementsByClassName("hide-link"); for(b in a){if(b<=a.length)
document.getElementsByClassName("hide-link")[b].className=document.getElementsByClassName("hide-link")[b].className.replace("hide-link","")}
```

In bookmarklet form:

```js
javascript:(function()%7Bvar a %3D document.getElementsByClassName("hide-link")%3B for(b in a)%7Bif(b<%3Da.length)%0Adocument.getElementsByClassName("hide-link")%5Bb%5D.className%3Ddocument.getElementsByClassName("hide-link")%5Bb%5D.className.replace("hide-link"%2C"")%7D%7D)()%3B
```

Just run the script and the hidden options will show up. Enjoy!

### STAR test

STAR tests are handled through Renaissance Learning, which doesn't have any browser restrictions. Access it [here](https://global-zone08.renaissance-go.com/studentportal/) and sign in with your normal credentials. If a monitor password is needed to start the test, enter `admin` (very secure, I know).

## California
All state assesments done in Californian public schools are done with California Assessment of Student Performance and Progress (CAASPP) secure test browser. This "secure" browser acts like every other test browser, limiting the use of the system.

### CAASPP
Luckily, you literally don't even need to use the secure browser! The login page is available at https://ca.cambiumtds.com/student, and from my understanding, you are able to access everything you normally would on the test browser, without restrictions.
