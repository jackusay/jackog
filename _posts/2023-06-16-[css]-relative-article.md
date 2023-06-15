---
published: true
---
## A New Post

* show title, intro, image in big screen
* show only title, intro in small screen



![2023-06-16 00_59_07-創意相關文章｜親子天下 - Brave.jpg]({{site.baseurl}}/img/2023-06-16 00_59_07-創意相關文章｜親子天下 - Brave.jpg)

![2023-06-16 00_59_21-創意相關文章｜親子天下 - Brave.jpg]({{site.baseurl}}/img/2023-06-16 00_59_21-創意相關文章｜親子天下 - Brave.jpg)

---

```html
<div class="wrap"><a href=""></a> <p></p> </div>
```

the wrap need limit height:
```css
height: 120px;
```

the intro use multi line ellipsis.

result:

the layout will overlay because <a> wrap.

solve:

m1. <a> limit one line.
    https://stackoverflow.com/questions/17779293/css-text-overflow-ellipsis-not-working

m2. canceal intro when small screen.