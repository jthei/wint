# WINT (browser digital signage system)

This is a digital signage system that is available in only browser. It is possible to deliver a plurality of information by the display unit there are two news display part and the content display section on the screen. Contents can be also display dynamic content for content that can be displayed can also display HTML not only the image, to get the content sequentially display. In order to be updated as necessary each time around the display schedule, content with news display part and the content display unit is possible to change the display contents without stopping the system.

## Demo

[http://web.sfc.wide.ad.jp/~ema/wint/](http://web.sfc.wide.ad.jp/~ema/wint/)

## Installation method

Write the URL of the JSON file that shows the display schedule to newsJsonUrl and contentJsonUrl of config.js, to publish on the server this directory. Please access the directory then, has been published in Google Chrome. I can F11 key on Windows, and shift + command + F on the Macintosh full screen display in Google Chrome.

Because in this system, you are not using any server-side programming, and does not require any special environmental settings on the server.

## Edit Settings

such as setting the animation of the display content when switching content portion and the URL of the schedule file, the news section has been described in the config.js. Also, I have specified character content section in style.css, the news section, size, and background of the margin. Please change these values ​​to suit your environment.

## I want to specify a schedule

Display schedule and news content will interpret on the basis of the output of the JSON obtained from the URL of newsJsonUrl and contentJsonUrl of config.js. The format of this JSON will be as follows. In addition, we now schedule does not change it over time for this JSON is held as a file in the code but, separately, the dynamic schedule by developing a program that outputs a JSON server-side programming Such systems can be changed basis will be completed.

### JSON specification of content schedule

    [
        {
            "duration": 10,
            "type": "iframe",
            "url": "http://localhost/wint/sample.html"
        },
        {
            "duration": 10,
            "type": "img",
            "url": "http://localhost/wint/sample.png"
        }
    ]

<dl>
<dt>duration</dt>
<dd>The length of the display time of the content, in seconds</dd>
<dt>type</dt>
<dd>img or iframe</dd>
<dt>url</dt>
<dd>URL that content exists</dd>
</dl>

### JSON specification of News Schedule

    [
        "text1",
        "text2",
        "text3"
    ]

## Test environment

This program has confirmed the launch at the (Mac OS X) Google Chrome version 25.0.1364.160.

## License

I am according to the MIT license. Please refer to the license.txt in use.

## Specifications of the development and operation on

*I will re-acquire the display when the end of each schedule schedule file content, news. Edit the schedule is not necessarily be reflected immediately for that.
*The size of the display of the content section while maintaining the aspect ratio, it has expanded into so as not to exceed the screen.
*For cache measures, we change the URL by adding or "'? Timestamp =' + date and time" and "'& timestamp =' + date and time" to the end of the URL at the time of acquisition to retrieve the JSON indicating the schedule. The determination of whether delimiter is and whether it is?, I am determined character? On whether or not are included in the URL of the schedule file.
*When you are viewing the content, it is the specification to get the content to be displayed next in the background. Therefore, because it does not receive the content at the stage of the content display, smooth becoming possible to switch the screen. There is that the content of the following does not appear in the smooth reception rate of the content is slow rarely, please adjust the line environment, such as with the server that owns the content if you have these.
*I am using an iframe of HTML tags to display the HTML page. Therefore, if it is set to "deny" the HTTP header "X-Frame-Options" on the display destination page, you will not be able to be displayed.

