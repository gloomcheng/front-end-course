# 套用 CSS 樣式的方法

有時我們可能會誤解成 CSS 是指 `.css` 的檔案，其實並不然，上述在 HTML 元素內使用 `style` 屬性的方法，就是使用了 CSS 。要使用 CSS，我們可以利用下列的三種方式：

## 行內套用

行內套用（inline style sheets）是指直接加在 HTML 元素內，必須使用 `style` 屬性來為該元素添加樣式效果。

```html
<p style="color:red; background:yellow; font-weight:bold;">
這個段落會被顯示為黃底紅字粗體。
</p>
```

預覽結果：
<p style="color:red; background:yellow; font-weight:bold;">
這個段落會被顯示為黃底紅字粗體。
</p>

## 嵌入套用

用行內套用的問題是仍然無法達到內容結構跟呈現樣式分開管理，也就是說，如果你要調整文字顏色的話，你還是得打開 HTML 文件來修改；此外，如果我們要對多個段落（`<p>`）設定相同的樣式時，則必須為每個 `<p>` 元素都設定 `style` 屬性。

嵌入套用（embedding style sheets）則可以稍稍改善這個問題。嵌入套用必須寫在 `<head></head>` 元素內，如下所示。

```html
<head>
  <style type="text/css">
  <!-- 簡寫成 <style> 也可以 -->
    p {
      color: red;
      background: yellow;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <p>這個段落會被顯示為黃底紅字粗體。</p>
</body>
```

使用嵌入套用方式，雖然我們要修改樣式時仍然要打開 HTML 文件出來編修，但至少可以不用針對每個元素做樣式的修改，也就是說，我們只要改 `p { ... }` 這裡面的樣式設定就可以了。

## 外部套用

外部套用（external style sheets）則是讓我們可以徹底將 HTML 文件與 CSS 樣式分離的做法，也就是說，我們可以在 HTML 文件內宣告說我們要從哪個外部檔案（`.css`）載入樣式表設定，這樣一來，若是我們只要改呈現樣式的話，我們就只要修改那個外部樣式表檔案即可。

外部套用的使用方式一樣是得寫在 `<head></head>` 元素內，使用 `<link>` 元素來加入外部檔案，如下所示。

```html
<head>
  <link href="custom.css" type="text/css" rel="stylesheet" />
</head>
```

除了使用 `<link>` 元素之外，我們也可以用匯入檔案的寫法來套用外部的樣式表檔案，如下所示。不過目前已經較少使用 `@import` 的寫法了，所以只需要記得 `<link>` 的用法就可以了。

```html
<head>
  <style type="text/css">
    @import url("custom.css");
  </style>
</head>
```

經過上面在 HTML 文件宣告好要從哪個檔案讀取樣式設定後，接下來，我們只需要在那個檔案（上例是指 `custom.css` 檔案）寫進樣式設定，如下所示。

```css
p {
  color: red;
  background: yellow;
  font-weight: bold;
}
```