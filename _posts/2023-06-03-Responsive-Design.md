---
published: true
---

## Viewport

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

![2023-06-04 00_37_48-HTML Responsive Web Design - Brave.jpg]({{site.baseurl}}/img/2023-06-04 00_37_48-HTML Responsive Web Design - Brave.jpg)

## Responsive Images

If the CSS width property is set to 100%, the image will be responsive and scale up and down:
```html
<img src="img_girl.jpg" style="width:100%;">
```

the image can be scaled up to be larger than its original size. A better solution, in many cases, will be to use the max-width property instead.

```html
<img src="img_girl.jpg" style="max-width:100%;height:auto;">
```

## `<picture>` Show Different Images Depending on Browser Width

## Media Queries

With media queries you can define completely different styles for different browser sizes.

source: https://www.w3schools.com/html/html_responsive.asp