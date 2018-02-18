[toc](README.md)

# RESPONSIVE IMAGES

> **DON'T ASSUME THE VIEWPORT SIZE WILL ALWAYS STAY THE SAME**

* When using images on the web consider file size!
* Don't use fixed widths for images, e.g. max-width: <percent>
* use `calc` to calculate widths and mix absolute and relative positioning


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