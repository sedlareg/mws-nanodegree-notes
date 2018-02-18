[toc](README.md)

# RESPONSIVE IMAGES

> **DON'T ASSUME THE VIEWPORT SIZE WILL ALWAYS STAY THE SAME**

* When using images on the web consider file size!
* Don't use fixed widths for images, e.g. max-width: <percent>
* Use `calc` to calculate widths and mix absolute and relative positioning
* Use jpg/png for photographic images
* Use png rather than gif
* Use svg if you can
* Images need to be only as large as they will be displayed
* Reduce the number of requests (Latency > Bandwidth)
  The higher the bandwidth it will not reduce the page load time. It flattens  
  out. The smaller the latency it will reduce and improve page load time.
  But beware of the new [HTTP2](https://mattwilcox.net/web-development/http2-for-front-end-web-developers) protocol.


## Relative Sizing

**Example: Positioning 2 pics side by side**

```css
img {
	width: 50%;
}
```

**Example: Positioning 2 pics side by side with a space of 10px between**

In this example I use `calc` to calculate the width of the image. That is a good way to combine absolute and relative values.

```css
img {
	max-width: 320px;
	width: calc((100% -10px)/2);
	margin-right: 10px;
}
img:last-of-type {
	margin-right: 0;
}
```

**Example: Positioning 3 pics side by side**

Notice that we have to add spaces between the minus in the calculation otherwise it will not work.

```css
body {
  margin: 0;
}
img {
  float: left;
  /*
  Your code goes here!
  */
  width: calc((100% - 20px)/3);
  margin-right: 10px;
}
img:last-of-type {
  margin-right: 0;
}

```

## CSS UNITS
There are some unknown properties which are now widely supported.

Viewport height and width (vh, vw)
1vh = 1% of the viewport height
1vw = 1% of the viewport width

Viewport minimum (vmin)
Scales to the side which ever is smaller

Viewport maximum (vmin)
Scales to the side which ever is greater


## BACKGROUNDSIZE

cover:
The smaller dimension of the image fits into the container => larger dimension will be cut off

contain:
The larger dimension of the image fits into the container => image will be repeated on the smaller side

## INLINE IMAGES (SVG/DATA_URI)

* [SVGOptimiser](http://petercollingridge.appspot.com/svg-optimiser)
* [Trajans Column Example](https://upload.wikimedia.org/wikipedia/commons/6/6c/Trajans-Column-lower-animated.svg)
* [SVG Animation](https://codepen.io/chrisgannon/)

## SRCSET

**Example: The browser should download Den_Haag_2x.jpg if it is a 2x display and Den_Haag_1x.jpg if it is a 1x display.**
```
<img class="dpi"
  src="images/Den_Haag_2x.jpg"
  srcset="images/Den_Haag_2x.jpg 2x, images/Den_Haag_1x.jpg 1x"
  alt="Den Haag Skyline">
```

**Example: Tell the browser that Australia_1280w.jpg is 1280px wide and Australia_640w.jpg is 640px wide so that the browser can choose the best one to download.**
```
<img class="w"
  src="images/Australia_1280w.jpg"
  srcset="images/Australia_1280w.jpg 1280w, images/Australia_640w.jpg 640w"
  alt="Australia from Space">
```

**Example: Tell the browser that it has the option of using Coffee_1280w.jpg and Coffee_640w.jpg, which have widths of 1280px and 640px respectively. Tell the browser that the image will display at 50vw if the page is 960px wide or smaller, otherwise the image displays at 100vw**

``` 
<style>
img {
  width: 100vw;
  max-width: 100%;
}
.w {
  transition: width 0.5s;
}
@media screen and (max-width: 960px) {
  .w {
    width: 50vw;
    margin-left: auto;
    margin-right: auto;
    display: block;
  }
}
</style>
<img class="w" src="images/Coffee_1280w.jpg" alt="Coffee by Amy March from Turkey" sizes="(max-width: 960px) 50vw, (min-width: 961px) 100vw" srcset="images/Coffee_1280w.jpg 1280w, images/Coffee_640w.jpg 640w"> 
```