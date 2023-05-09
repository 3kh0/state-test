# State Testing Unrestricted
**Ways to take state tests unrestricted.**

We are trying to get almost every state, if you have a different state, open a issue with the title of your state and provide AS MUCH DETAIL AS POSSIBLE about how you take your state tests.

## North Carolina
~~This is the first one bc I live in that state lol~~

The first thing you need to know is the way that the NCTest app was made was really stupid, it pretty much just iframes a existing page that you can search on google

![image](https://github.com/3kh0/state-test/assets/58097612/5b462bbb-4639-4919-8608-c3fe95ab5836)

The link there in question is [data.ncsu.edu/nctest/Destination.html](https://data.ncsu.edu/nctest/Destination.html), but if you click on the NCTest login, you would be blocked from logging in with this message.

![image](https://github.com/3kh0/state-test/assets/58097612/ee173148-b345-4e45-93f0-68ae06aefbf5)

Thank goodness the devs behind it for some reason added comments to their code, so we can exploit this. This function checks the user agent and deterimes if the test taker is in a "secure" testing environment. This only checks the first 6 characters of the user agent and if it is `NCTest`. Note this is a very simple way of how it works, so here are two ways to bypass and get this running.

### The easy method.

This is a much easy way without having to spoof useragents, this also depends if you can install the app on your device, this can work on Windows and Linux, but sometimes it does break, relaunching does seem to fix the issue of getting blocked.

1. Get the [NCTest App](https://chrome.google.com/webstore/detail/nctest/gekbonallhcfalincpgmjcipmjehfhlh/) from the Chrome Web Store
2. This step depends on your OS,

**If you are on a Chromebook**
1. Open the Launcher ![image](https://github.com/3kh0/state-test/assets/58097612/b6665d29-17d7-468a-a56d-facbbfd78ce5)
2. Locate the NCTest App and click on it
![image](https://github.com/3kh0/state-test/assets/58097612/8f4bb622-b483-4d5f-aca0-b917283570e3)
3. Click the NCTest login (or whatever you need the app for)
4. Profit

**If you are on Linux/Windows**
1. Go to `chrome://apps`
2. Click on the NCTest App
3. Click the NCTest login (or whatever you need the app for)

> **Note**
> If it still shows the block scren, close the app and reopen it.

In this app, you can use keybinds suck as `alt`+`tab` to change windows while taking the test. I did not figure out how to resize the window, it seems it is locked to fill the screen.

![image](https://github.com/3kh0/state-test/assets/58097612/3593097f-092b-475b-8b03-db8329188ae1)


### The hard method.

Coming soon, still researching on how this works and the best way to do it.

Further Reading:
- https://defcon.social/@3kh0/110293819888798643
