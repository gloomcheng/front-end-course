# CSS 選擇器

選擇器的寫法規則如下：

```css
selector { property: value; }
```
+ `selector`：選擇器，通常是 HTML 文件中的元素，例如 `<html>`、`<body>`、`<h1>`、`<p>` 等
+ `property`：屬性，也就是用來控制選擇器的樣式，例如 `font-family`、`font-size`、`color` 等
+ `value`：設定值，就是屬性的設定值，例如 `font-size: 12px`，就是將 `font-size` 屬性設定為 `12px`

在上面的例子中，我們其實已經有運用到選擇器（selector）的概念了。選擇器是用來指定我們要對 HTML 文件的「哪些元素」套用樣式效果的概念，如同前述寫到的 `p { ... }` 就有運用到 CSS 選擇器的用法，也就是會選擇到 `<p>` 元素，所以這份 CSS 樣式設定就會套用到 HTML 文件中的所有 `<p>` 元素。

CSS3 標準文件定義了以下幾種不同類型的選擇器：

## 元素選擇器（Type Selector）