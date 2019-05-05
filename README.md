# FastClick #

FastClick is a simple, easy-to-use library for eliminating the 300ms delay between a physical tap and the firing of a `click` event on mobile browsers. The aim is to make your application feel less laggy and more responsive while avoiding any interference with your current logic.

FastClick is developed by [FT Labs](http://labs.ft.com/), part of the Financial Times.

本库由[L.S](https://github.com/LiZ2z)修改


*注意: 到2015年底，大多数移动浏览器 **尤其是Chrome和Safari** 不再有300ms的触摸延迟，因此fastclick对较新的浏览器没有任何好处，并且有可能在应用程序中引入[bugs](https://github.com/ftlabs/fastclick/issues)。仔细考虑是否真的需要使用它。*

## Why does the delay exist? ##

According to [Google](https://developers.google.com/mobile/articles/fast_buttons):

> ...mobile browsers will wait approximately 300ms from the time that you tap the button to fire the click event. The reason for this is that the browser is waiting to see if you are actually performing a double tap.


## 什么时候不需要 ##

FastClick在桌面端的浏览器不会起作用。


在安卓系统上的 Chrome 32+ 浏览器中，如果在[viewport meta 标签](https://developer.mozilla.org/en-US/docs/Mobile/Viewport_meta_tag)中加入`width=device-width`属性，就不会有300ms点击延迟，所以也不需要。

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

同样的道理也适用于Android上的Chrome(所有版本)，在viewport meta 标签中有"user-scalable=no"。但是请注意，"user-scalable=no"也会禁用双指缩放，这可能导致可访问性不是很好（无所谓了）。

IOS11（未测试，ios12确定不需要）之后的safari也不用了，但是其它使用safari做内核的app还是有问题，所以还是要用。

For IE11+, you can use `touch-action: manipulation;` to disable double-tap-to-zoom on certain elements (like links and buttons).  For IE10 use `-ms-touch-action: manipulation`.


## Compatibility ##

The library has been deployed as part of the [FT Web App](http://app.ft.com/) and is tried and tested on the following mobile browsers:

* Mobile Safari on iOS 3 and upwards
* Chrome on iOS 5 and upwards
* Chrome on Android (ICS)
* Opera Mobile 11.5 and upwards
* Android Browser since Android 2
* PlayBook OS 1 and upwards


## 使用 ##

### ES6 ###

```js
import fastClick from '@nuofe/fastclick';
fastClick.attach(document.body, [options]);
```
