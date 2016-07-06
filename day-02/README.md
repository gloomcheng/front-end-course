# 第二天

## HTML 文件的樣式

經過第一天課程的介紹，我們已經知道要開發一個網頁內容，可以運用 `<h1>` ~ `<h6>`、`<p>`、`<ul>`、`<ol>`、`<table>` 等 HTML 元素製作出網頁的內容，然而卻沒有針對網頁外觀呈現樣式專用的元素。例如，我們似乎無法很簡單地只撰寫 HTML 元素就可以定義出兩欄式或三欄式的網頁設計樣式。

但網頁光只有文字內容實在太單調了，於是有段時間[各家瀏覽器大開樣式戰爭](http://irw.ncut.edu.tw/peterju/css.html#handicap)，制定出多種與外觀樣式有關但卻不具語義的標記元素，使得原本單純的 HTML 變成複雜且不易閱讀。例如下面這段以 [`<font>`](https://developer.mozilla.org/zh-TW/docs/Web/HTML/Element/font) 標記元素的寫法，就是直接在 HTML 文件中設定文字字體、大小及顏色，雖然可以讓這段文字具有外觀上的意義，但就 HTML 文件本身的結構來說，`<font>` 對搜尋引擎來說就沒有太多的意義。

```html
<font size="+3" face="細明體" color="red">標題文字</font>
```

就搜尋引擎的角色來說，只需要知道 HTML 文件寫了什麼內容，例如標題是什麼、文章內容是什麼，以及哪些是共用的選單、哪些是頁尾資訊等。也就是說，如果搜尋引擎可以「讀得出」文章的結構及語義的話，那它就可以略過部分沒那麼重要內容，因為搜尋引擎本來就應該是針對內容進行搜尋，才會找尋出符合使用者的期待的搜尋結果。因此，剛剛使用 `<font>` 元素設計的頁面，就使用者觀看到的頁面確實會有文字調整的效果，但對搜尋引擎來說，`<font>` 這個元素只是用來調整文字的樣式效果，本身並無任何語義，因此這個 HTML 元素看來就可有可無。

為了解決前述問題，W3C 組織在制定 HTML4 標準的時候，希望讓 HTML 文件可以聚焦在「內容」上，於是[加入了排版用的元素 `<div>` 及 `<span>`](http://irw.ncut.edu.tw/peterju/css.html#return)，同時導入了 [CSS（Cascading Style Sheets，階層式樣式表）](https://zh.wikipedia.org/wiki/%E5%B1%82%E5%8F%A0%E6%A0%B7%E5%BC%8F%E8%A1%A8) 的設計，用來專職處理網頁的外觀呈現效果。這也是現代網頁設計都會同時談 HTML + CSS 的原因，這樣的做法不但可以讓網頁內容易於維護（例如我們要套用新的設計樣式，只需要改 CSS 就好，而不需重新修改 HTML 文件），同時也讓搜尋引擎更能理解網頁的內容（因為 HTML 文件裡只會留下具有語義意思的元素和內容）。至於我們要如何改用 CSS 來控制頁面的呈現效果呢？我們來將上面範例中的 `<font>` 元素棄用，同時用 CSS 樣式表的方式來改寫看看，如下所示。

```html
<h1 style="font-size: 32px; font-family:'細明體'; color: red">標題文字</h1>
```
看起來很熟悉吧，沒錯，其實我們在第一天的課程內容裡已經稍微提到一些 CSS 樣式表設計的概念了。

## 套用樣式

有時我們可能會誤解成 CSS 是指 `.css` 的檔案，其實並不然，上述在 HTML 元素內使用 `style` 屬性的方法，就是使用了 CSS 。要使用 CSS，我們可以利用下列的三種方式：

### 行內套用

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

### 嵌入套用

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

### 外部套用

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

## CSS 選擇器

選擇器的寫法規則如下：

```css
selector { property: value; }
```
+ `selector`：選擇器，通常是 HTML 文件中的元素，例如 `<html>`、`<body>`、`<h1>`、`<p>` 等
+ `property`：屬性，也就是用來控制選擇器的樣式，例如 `font-family`、`font-size`、`color` 等
+ `value`：設定值，就是屬性的設定值，例如 `font-size: 12px`，就是將 `font-size` 屬性設定為 `12px`

在上面的例子中，我們其實已經有運用到選擇器（selector）的概念了。選擇器是用來指定我們要對 HTML 文件的「哪些元素」套用樣式效果的概念，如同前述寫到的 `p { ... }` 就有運用到 CSS 選擇器的用法，也就是會選擇到 `<p>` 元素，所以這份 CSS 樣式設定就會套用到 HTML 文件中的所有 `<p>` 元素。

CSS3 標準文件定義了以下幾種不同類型的選擇器：

### 元素選擇器（Type Selector）
