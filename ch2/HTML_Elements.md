# HTML 元素

要能夠開發、編寫網頁內容，就一定要熟知 HTML 元素，並瞭解各種 HTML 元素的用法。在開始下面章節前，建議你應該先瀏覽下「[HTML 元素](https://developer.mozilla.org/zh+TW/docs/Web/HTML/Element)」的頁面，以對 HTML 元素有初步的瞭解，同時也注意下哪些元素是只適用在 HTML5，而哪些元素又只適用在 HTML4。還有，因為 HTML 文件開發的前提應該是要適用於各種瀏覽器，所以也[應避免使用過時的語法](https://developer.mozilla.org/zh-TW/docs/Web_%E9%96%8B%E7%99%BC/Historical_artifacts_to_avoid)，以維持 HTML 文件的可讀性。

接下來，我們要進入學習撰寫 HTML 文件的內容了，請試著使用以下章節介紹的 HTML 元素自行運用編寫成 HTML 文件。

## 文字編排

### 標題

```html
<h1></h1>
<h2></h2>
<h3></h3>
<h4></h4>
<h5></h5>
<h6></h6>
```
+ [範例](http://jsbin.com/nufelagexo/edit?html,output)

### 段落

```html
<p></p>
```

+ [範例](http://jsbin.com/vekopimuka/edit?html,output)

### 粗體

```html
<b></b>
```

+ [範例](http://jsbin.com/difopimisu/edit?html,output)

### 斜體

```html
<i></i>
```

+ [範例](http://jsbin.com/jokiwirigo/edit?html,output)

### 上標

```html
<sup></sup>
```

+ [範例](http://jsbin.com/kigixocure/edit?html,output)

### 下標

```html
<sub></sub>
```

+ [範例](http://jsbin.com/pujajecaqi/edit?html,output)

### 斷行

```html
<br /> 或 <br>
```

+ [範例](http://jsbin.com/xesegojojo/edit?html,output)

### 水平線

```html
<hr /> 或 <hr>
```

+ [範例](http://jsbin.com/hinodideja/edit?html,output)

## 項目符號

### 有序列表

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

### 無序列表

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

### 自定義列表

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

## 連結

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

## 圖片

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

## 表格

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
