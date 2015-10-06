---
author: benjchristensen
comments: true
date: 2010-08-28 06:01:13+00:00
layout: post
slug: trigger-native-javascript-events-with-prototype-js
title: Trigger Native Javascript Events with Prototype.js
---

After much searching and playing with various solutions, I found one at this page:

http://stackoverflow.com/questions/590289/javascript-event-that-fires-without-user-interaction/590339#590339

This provides an easy method for programmatically invoking native events such as "onchange".

Here it is:

[sourcecode language="javascript" light="true" wraplines="true"]

// this supports trigger native events such as 'onchange' 
// whereas prototype.js Event.fire only supports custom events
function triggerEvent(element, eventName) {
    // safari, webkit, gecko
    if (document.createEvent)
    {
    var evt = document.createEvent('HTMLEvents');
    evt.initEvent(eventName, true, true);</code>

        return element.dispatchEvent(evt);
    }

    // Internet Explorer
    if (element.fireEvent) {
        return element.fireEvent('on' + eventName);
    }
}

[/sourcecode]


This is primarily to deal with prototype.js not allowing the firing of native events (which jQuery does).

Here is another approach I found but have not tried which adds the capability to prototype.js: [event.simulate.js](http://github.com/kangax/protolicious/blob/5b56fdafcd7d7662c9d648534225039b2e78e371/event.simulate.js)
