# 網路運作原理 

當我們打開瀏覽器在「網址列」輸入 `tw.yahoo.com`，接著就會看到「Yahoo 奇摩」的頁面出現，看似簡單平凡的動作，其實瀏覽器和網路在背後做了很多的工作。











## 撰寫 HTML 文件

接下來，我們要進入學習撰寫 HTML 文件的內容了，請試著使用以下章節介紹的 HTML 元素自行運用編寫成 HTML 文件。

### 文字編排

#### 標題

```html
<h1></h1>
<h2></h2>
<h3></h3>
<h4></h4>
<h5></h5>
<h6></h6>
```
+ [範例](http://jsbin.com/nufelagexo/edit?html,output)

#### 段落

```html
<p></p>
```

+ [範例](http://jsbin.com/vekopimuka/edit?html,output)

#### 粗體

```html
<b></b>
```

+ [範例](http://jsbin.com/difopimisu/edit?html,output)

#### 斜體

```html
<i></i>
```

+ [範例](http://jsbin.com/jokiwirigo/edit?html,output)

#### 上標

```html
<sup></sup>
```

+ [範例](http://jsbin.com/kigixocure/edit?html,output)

#### 下標

```html
<sub></sub>
```

+ [範例](http://jsbin.com/pujajecaqi/edit?html,output)

#### 斷行

```html
<br /> 或 <br>
```

+ [範例](http://jsbin.com/xesegojojo/edit?html,output)

#### 水平線

```html
<hr /> 或 <hr>
```

+ [範例](http://jsbin.com/hinodideja/edit?html,output)

### 項目符號

#### 有序列表

有序列表就是指會自動在項目前加上數字編號。

```html
<ol>
  <li></li>
  <li></li>
  <li></li>
</ol>
```

`<ol>` 即 ordered list 的縮寫，可包含 `<li>` 元素來指定每個項目資料。

+ [範例](http://www.w3schools.com/tags/tryit.asp?filename=tryhtml_lists)

#### 無序列表

無序列表就是指會自動在項目前加上圓點（bullet）。

```html
<ul>
  <li></li>
  <li></li>
  <li></li>
</ul>
```

`<ul>` 即 unordered list 的縮寫。

+ [範例](http://www.w3schools.com/tags/tryit.asp?filename=tryhtml_lists4)

#### 自定義列表

自定義列表適用於專有名詞。

```html
<dl>
  <dt>咖啡</dt>
  <dd>黑色的熱飲</dd>
  <dt>牛奶</dt>
  <dd>白色的冷飲</dd>
</dl>
```

`<dt>` 用在要被定義的專有名詞，而 `<dd>` 則是該專有名詞的解釋說明。

+ [範例](http://www.w3schools.com/tags/tryit.asp?filename=tryhtml_dd_test)

### 連結

```html
<a href="http://www.google.com" target="_blank">點按後可連到 Google 網站</a>
```
`<a>` 元素通常會使用的屬性有：

+ `href`：設定 `<a>` 元素的連結網址，可使用的網址類型有
  + 絕對網址：如 `http://www.google.com`
  + 相對網址：如 `./index.html`
  + 錨點：如 `#summary`，就會跳到同頁面中 `id` 為 `summary` 的元素（例如跳到 `<h2 id="summary"></h2>`）
  + Email：如 `mailto:gloomcheng@gmail.com`，Email 的連結除了可以設定收件者 Email 之外，還可以同時設定 Email 的主旨、本文，甚至也可以同時設定副本、密件副本的收件者 Email，例如
   `<a href="mailto:gloomcheng@gmail.com?subject=感謝您的貢獻&body=謝謝您撰寫這份教材，我看完之後真的有比較理解網頁的運作原理及網頁的開發方式">寄信感謝作者</a>`，如果你想進一步瞭解怎麼產生 Email 連結，可使用「[Mailto 產生器](http://www.mailto.co.uk/)」
+ `target`：設定在哪裡開啟連結，較常見的有 `_blank` 表示會在新的瀏覽器分頁開啟此連結，或 `_self`（預設值）表示會在目前的瀏覽器分頁開啟此連結

+ <a href="mailto:gloomcheng@gmail.com?subject=感謝您的貢獻&body=謝謝您撰寫這份教材，我看完之後真的有比較理解網頁的運作原理及網頁的開發方式">寄信感謝作者</a>

### 圖片

```html
<figure>
  <img src="http://akamaicovers.oreilly.com/images/9780596527327/lrg.jpg"
    alt="HTML & XHTML: The Definitive Guide book cover"
    title="HTML & XHTML: The Definitive Guide"
    width="300" />
  <figcaption>Written by Chuck Musciano, Bill Kennedy</figcaption>
</figure>
```

<figure>
  <img src="http://akamaicovers.oreilly.com/images/9780596527327/lrg.jpg"
    alt="HTML & XHTML: The Definitive Guide book cover"
    title="HTML & XHTML: The Definitive Guide"
    width="200" />
  <figcaption>Written by Chuck Musciano, Bill Kennedy</figcaption>
</figure>
<br />

`<img>` 元素通常會使用的屬性有：

+ `src`：指定圖片來源的網址，同樣可以使用**絕對路徑**和**相對路徑**來標示圖片的位置
+ `alt`：圖片替代文字，當圖片無法成功顯示時，會在頁面上看到 alt 文字
+ `title`：圖片標題文字，當滑鼠移經圖片時會自動顯示的文字
+ `width`：圖片寬度，若無設定則會自動設定為圖片原本的寬度
+ `height`：圖片高度，若無設定則會自動設定為圖片原本的高度

`<figcaption>`<img src="https://www.w3.org/html/logo/downloads/HTML5_Badge_32.png" alt="HTML5 LOGO" width="16" height="16"> 則是用來呈現圖說的元素，為 HTML5 新增加的元素。

以下的案例則是用來說明 `alt` 與 `title` 的差異，請注意，下面的圖片應已失效無法存取，所以應該會在頁面上看到 alt 文字而無法正確顯示圖檔；而當你將滑鼠移到圖片上停留時，將會看到 title 文字。

```html
<img src="http://artemij.com/images/react_essentials_book_cover.jpg"
    alt="React.js Essentials book cover"
    title="Written by Artemij Fedosejev"
    width="300" />
```

<img src="http://artemij.com/images/react_essentials_book_cover.jpg"
    alt="React.js Essentials book cover"
    title="Written by Artemij Fedosejev"
    width="300" />

### 表格

```html
<table>
  <tr>
    <th>Tens</th>
    <th>Hundreds</th>
    <th>Thousands</th>
  </tr>
  <tr>
    <td>10</td>
    <td>20</td>
    <td>30</td>
  </tr>
  <tr>
    <td>100</td>
    <td>200</td>
    <td>300</td>
  </tr>
  <tr>
    <td>1000</td>
    <td>2000</td>
    <td>3000</td>
  </tr>
</table>
```

<table>
  <tr>
    <th>Tens</th>
    <th>Hundreds</th>
    <th>Thousands</th>
  </tr>
  <tr>
    <td>10</td>
    <td>20</td>
    <td>30</td>
  </tr>
  <tr>
    <td>100</td>
    <td>200</td>
    <td>300</td>
  </tr>
  <tr>
    <td>1000</td>
    <td>2000</td>
    <td>3000</td>
  </tr>
</table>

其中 `<table>` 是定義表格的元素，在該元素內再使用 `<tr>` 來定義表格的「列」（row），以及使用 `<td>` 來定義表格的「欄」（column）。至於 `<th>` 則通常只有第一列會使用，是用來定義表格標題列的欄位資料。

一般表格只需要使用到 `<table>`、`<tr>`、`<td>` 就可以了，但為了讓表格更具語義，我們通常還會再使用 `<thead>` 及 `<tbody>` 來區分表格標題與表格內文。

```html
<table>
  <thead>
    <tr>
      <th>Tens</th>
      <th>Hundreds</th>
      <th>Thousands</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>10</td>
      <td>20</td>
      <td>30</td>
    </tr>
    <tr>
      <td>100</td>
      <td>200</td>
      <td>300</td>
    </tr>
    <tr>
      <td>1000</td>
      <td>2000</td>
      <td>3000</td>
    </tr>
  </tbody>
</table>
```

如果我們想製作出跨欄或跨列的表格，就可以在 `<td>` 元素加上 `rowspan` 或 `colspan` 屬性來設定跨列或跨欄。

##### 牛刀小試

試試看使用文字編輯器把下面的表格編寫出來。

<table>
  <thead>
    <tr>
      <th>名稱</th>
      <th>品種</th>
      <th>數量</th>
      <th>小計</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="3">A</td>
      <td>x</td>
      <td>1,500</td>
      <td rowspan="3">4,000</td>
    </tr>
    <tr>
      <td>y</td>
      <td>1,300</td>
    </tr>
    <tr>
      <td>z</td>
      <td>1,200</td>
    </tr>
    <tr>
      <td rowspan="2">B</td>
      <td>o</td>
      <td>3,000</td>
      <td rowspan="2">5,000</td>
    </tr>
    <tr>
      <td>p</td>
      <td>2,000</td>
    </tr>
    <tr>
      <td colspan="2">合計</td>
      <td colspan="2">9,000</td>
    </tr>
  </tbody>
</table>

### 排版

在網頁開發實例中，我們會經常看到 `<div>` 與 `<span>` 元素的運用，這兩個元素不像前面介紹的元素有特定的功能和適用場合，純粹是為了便於排版（layout）所用。例如，我們想設計一個頁面有「頁首」、「左側欄」、「主要內容」和「頁尾」的排版樣式，我們就會利用 `<div>` 元素來設計出 HTML 文件，再透過 CSS 樣式表的套用，排出我們想要的樣式。

```html
<body>
  <div style="border: 1px solid #ccc; background: pink;">
    <h1>這裡是網頁標題</h1>
    <p>歡迎來到我的網站</p>
  </div>
  <div style="border: 1px solid #ccc; background: blue; min-height: 200px;">
    <div class="left-sidebar" style="border: 1px solid #ccc; background: green; float: left; min-height: 200px; width: 20%;">
      <p>這裡是側邊欄</p>
    </div>
    <div class="main-content" style="border: 1px solid #ccc; background: yellow; float: left; min-height: 200px; width: 60%;">
      <p>這裡是主要內容段落</p>
      <p>這裡是主要內容段落</p>
      <p>這裡是主要內容段落</p>
      <p>這裡是主要內容段落</p>
      <p>這裡是主要內容段落</p>
    </div>
    <div class ="right-sidebar" style="border: 1px solid #ccc; background: green; min-height: 200px;">
      <p>這裡是右側欄</p>
    </div>
  </div>
  <div style="border: 1px solid #ccc; background: pink;">
    <p>這裡是頁尾資訊</p>
  </div>
</body>
```

由於 HTML4 大量使用 `<div>` 來進行網頁排版的設計，造成 HTML 文件失去該有的語義，所以 HTML5 加入許多新的元素，就是為了便於排版所設計的。

![HTML5 排版元素](http://www.w3schools.com/html/img_sem_elements.gif)

+ `<header>`<img src="https://www.w3.org/html/logo/downloads/HTML5_Badge_32.png" alt="HTML5 LOGO" width="16" height="16">：定義文章的頁首資訊。請注意，與 `<head>` 不同，`<header>` 元素是放在 `<body>` 元素內
+ `<nav>`<img src="https://www.w3.org/html/logo/downloads/HTML5_Badge_32.png" alt="HTML5 LOGO" width="16" height="16">：用來存放導覽列的內容
+ `<section>`<img src="https://www.w3.org/html/logo/downloads/HTML5_Badge_32.png" alt="HTML5 LOGO" width="16" height="16">：可以定義文章的章節，用以區分不同章節的內容，例如第一章內可以有 `<h1>` 元素、第二章內也可以有 `<h1>` 元素，而這兩個 `<h1>` 元素都可以在其脈絡下提供適當的語義（早期沒有 `<section>` 元素，若文件內同時有兩個 `<h1>` 元素較無法從網頁原始碼看出個別元素代表的標題意義為何）
+ `<article>`<img src="https://www.w3.org/html/logo/downloads/HTML5_Badge_32.png" alt="HTML5 LOGO" width="16" height="16">：存放文章的主要內容
+ `<aside>`<img src="https://www.w3.org/html/logo/downloads/HTML5_Badge_32.png" alt="HTML5 LOGO" width="16" height="16">：提供內容相關的輔助內容，類似「側邊欄」的效果
+ `<footer>`<img src="https://www.w3.org/html/logo/downloads/HTML5_Badge_32.png" alt="HTML5 LOGO" width="16" height="16">：定義文章的頁尾資訊

##### 牛刀小試

試試看，將上述範例的網頁內容順序調整如下，然後透過修改 `style` 屬性來排出如下圖的效果。

```html
<body>
  <div style="border: 1px solid #ccc; background: pink;">
    <h1>這裡是網頁標題</h1>
    <p>歡迎來到我的網站</p>
  </div>
  <div style="border: 1px solid #ccc; background: blue; min-height: 200px;">
    <div class="main-content" style="">
      <p>這裡是主要內容段落</p>
      <p>這裡是主要內容段落</p>
      <p>這裡是主要內容段落</p>
      <p>這裡是主要內容段落</p>
      <p>這裡是主要內容段落</p>
    </div>
    <div class="left-sidebar" style="">
      <p>這裡是側邊欄</p>
    </div>
    <div class ="right-sidebar" style="">
      <p>這裡是右側欄</p>
    </div>
  </div>
  <div style="border: 1px solid #ccc; background: pink;">
    <p>這裡是頁尾資訊</p>
  </div>
</body>
</html>
```

![成果預覽](https://dl.dropboxusercontent.com/u/9320006/%E7%B6%B2%E9%A0%81%E6%8E%92%E7%89%88%E7%AF%84%E4%BE%8B.png)

### 嵌入其他網頁

```html
<iframe width="640" height="360"
  src="https://www.youtube.com/embed/vCKESBmlP9o"
  frameborder="0" allowfullscreen></iframe>
```

<iframe width="640" height="360" src="https://www.youtube.com/embed/vCKESBmlP9o" frameborder="0" allowfullscreen></iframe>

`<iframe>` 元素可用來將其他網頁內容的資訊嵌入到 HTML 文件，例如我們可以將 YouTube 影片或 Google 地圖嵌入到我們的網頁中。

## 課後練習

請運用今天課程學到的知識，試著編寫出類似下圖排版樣式的 HTML 文件。

![作業](https://dl.dropboxusercontent.com/u/9320006/%E5%8C%97%E5%95%86%20CDM%20%E5%AF%A6%E7%BF%92%E6%8B%9B%E5%8B%9F%E7%B6%B2%E7%AB%99.png)

+ [解答](sample-01/index.html)

## 參考資料

1. Uniform Resource Identifier (URI): https://en.wikipedia.org/wiki/Uniform_Resource_Identifier
2. Uniform Resource Locator (URL): https://en.wikipedia.org/wiki/Uniform_Resource_Locator
3. 浏览器的工作原理：新式网络浏览器幕后揭秘: http://www.html5rocks.com/zh/tutorials/internals/howbrowserswork/
4. HTML5: https://www.w3.org/TR/html5/
5. HTML5 Browser Support: http://www.w3schools.com/html/html5_browsers.asp
6. HTML5 準備好了:  http://www.cc.ntu.edu.tw/chinese/epaper/0010/20090920_1006.htm
7. HTML 5 與 HTML4 的差異與特色: http://inspiregate.com/programming/html+css/106+html+5+differences+and+characteristics+with+html4.html
