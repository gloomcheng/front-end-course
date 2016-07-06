# 第一天

## 網路運作原理

當我們打開瀏覽器在「網址列」輸入 `tw.yahoo.com`，接著就會看到「Yahoo 奇摩」的頁面出現，看似簡單平凡的動作，其實瀏覽器和網路在背後做了很多的工作。

### 統一資源定位符 (Uniform Resource Locator, URL)

首先，我們在網址列輸入的網址，正確的名稱叫做「[統一資源定位符](https://zh.wikipedia.org/wiki/%E7%BB%9F%E4%B8%80%E8%B5%84%E6%BA%90%E5%AE%9A%E4%BD%8D%E7%AC%A6)」，用來指向網際網路上的某個資源，也就是說，這個網址的功能就是讓瀏覽器知道要去找網際網路上的哪台電腦，以及跟它要回哪一個檔案回來供使用者查看。

URL 的格式為：`scheme:[//[user:password@]host[:port]][/]path[?query][#fragment]`

+ `scheme`：網路服務的類型，例如 `http`、`https`、`ftp` 等
+ `user`/`password`：登入該台網路主機所須的帳號、密碼，通常是 `ftp` 之類的服務才會限制登入
+ `host`：網站位置；通常會再細分成「子網域」+「網域」，例如 `www.google.com.tw` 的「網域」是 `google.com.tw`（通常是到 `.com.tw` 前），而「子網域」則是 `www`
+ `port`：主機連線的埠口，例如 `80`（`http`）、`443`（`https`）、`21`（`ftp`）等，你也可以查看「[TCP/UDP埠列表](https://zh.wikipedia.org/wiki/TCP/UDP%E7%AB%AF%E5%8F%A3%E5%88%97%E8%A1%A8)」進一步瞭解還有哪些服務
+ `path`：網址路徑，例如 `about.html`；如果沒有指定，預設會抓根目錄下的 `index.html`
+ `query`：查詢字串，通常是用於動態程式語言傳遞參數所用
+ `fragment`：錨點，可以快速指向到頁面特定段落的功能

接下來，我們以 `http://maps.google.com` 這個網址為例，練習拆解一下網址結構。這個網址的 `scheme` 是使用 `http`；因為開放給所有使用者瀏覽，所以不需要登入帳密（當然也有需要登入帳密才能查看的網站），不需設定 `user`/`password`；`path` 中的 `google.com` 是網域（domain）名稱、`maps` 是子網域（subdomain）名稱（或稱作主機名稱）；除非有特殊原因沒有採用預設 `port`，例如 `http://example.com:8080`，我們才需要手動輸入 `8080`，不然會直接補上預設值 `80`；`path` 沒設的話則會預設直接存取根目錄下的首頁。

### 網域名稱系統（Domain Name System, DNS）

輸入網址（URL）之後，那麼瀏覽器就可以透過網路到對方主機擷取網頁回來，並呈現成我們看到的頁面了嗎？沒這麼簡單！當我們輸入網址後，首先只是讓瀏覽器知道我們是想存取網路上的哪個資源，然而，在真正連線到對方主機前，還有一個難關要先跨過。

一樣以 `tw.yahoo.com` 為例，我們看到這個網址時都會知道這是指「Yahoo 奇摩」網站，但對電腦網路來說卻不是這樣的，電腦網路是認不得這個「[網域名稱](https://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D)」的，網域名稱只是方便我們人類記憶、溝通使用的代名詞，電腦網路只能認得網路上的唯一地址，也就是「[IP 位址](https://zh.wikipedia.org/wiki/IP%E5%9C%B0%E5%9D%80)」。

IP 位址有分兩種格式，分別是目前常見的 [IPv4](https://zh.wikipedia.org/wiki/IPv4) 及正在逐步推廣使用的 [IPv6](https://zh.wikipedia.org/wiki/IPv6)，而這個才是網路上識別電腦的唯一位址，你可以把 IP 位址想像成是電腦在網際網路上的門牌號碼，我們得透過這個門牌號碼才能找到這台電腦是位於哪個國家、哪個縣市、哪個城市，甚至是哪個建築物的哪個房間內。

因此當我們試圖存取 `tw.yahoo.com` 時，電腦其實不能知道這個網址的確切位址在哪裡，所以得先透過「[網域名稱系統](https://zh.wikipedia.org/zh+tw/%E5%9F%9F%E5%90%8D%E7%B3%BB%E7%BB%9F)」來進行網域和 IP 的轉換工作，並將 IP 位址回傳給你的電腦，這樣你的電腦才能接續從網路上找到對應的主機。

##### 牛刀小試

試試看在命令列介面（Windows 請打開 `cmd`、Mac 請打開 `iTerm`）下，輸入 `nslookup` 指令，查看 `www.yuntech.edu.tw` 的 IP 位址為何？

```bash
$ nslookup
> www.yuntech.edu.tw
```

### 排版引擎（Layout Engine）

當電腦透過 DNS 將網域轉換成 IP 位址，並成功與遠端電腦建立連線後，接下來就會把我們在網址輸入的資源請求送回來，同樣以在網址輸入 `tw.yahoo.com` 為例，當電腦透過 DNS 查詢得知其實是要連線到 `116.214.12.74` 後，就會送資源請求給對方的電腦，而這個資源請求就是指預設的 `index.html` 頁面。

當與對方建立連線後，對方電腦就會回傳 `index.html` 這個頁面的網頁原始碼回來，交由瀏覽器解讀。

請注意，此時取得的 HTML 文件並沒有包含這個網頁內的圖片、樣式表（stylesheet）及其他多媒體資源，而是在瀏覽器解讀 HTML 結構時，才會根據需求再向對方索取這些附加資源。

至於瀏覽器怎麼解讀 HTML 文件並產生成我們所閱讀的頁面呢？這就得提到瀏覽器的核心程式－「[排版引擎](https://zh.wikipedia.org/zh+tw/%E6%8E%92%E7%89%88%E5%BC%95%E6%93%8E)」。排版引擎一方面會解譯 HTML 文件的標記內容，另一方面會整理 CSS 樣式資料，然後再將兩者整合為一，產出最終的排版結果，如下圖所示。

![排版引擎的基本流程](http://www.html5rocks.com/zh/tutorials/internals/howbrowserswork/flow.png)

不同的排版引擎，其實作細節略有不同，例如下圖分別是 Webkit 排版引擎（使用於 Chrome / Safari 瀏覽器）與 Gecko 排版引擎（使用於 Firefox 瀏覽器）的流程圖。

![Webkit 基本流程](http://www.html5rocks.com/zh/tutorials/internals/howbrowserswork/webkitflow.png)

![Gecko 基本流程](http://www.html5rocks.com/zh/tutorials/internals/howbrowserswork/image008.jpg)

常用的瀏覽器採用的排版引擎不太相同：

+ [Microsoft Edge](https://zh.wikipedia.org/wiki/Microsoft_Edge)：[EdgeHTML](https://zh.wikipedia.org/wiki/EdgeHTML)
+ [Internet Explorer](https://zh.wikipedia.org/wiki/Internet_Explorer_4)：[Trident](https://zh.wikipedia.org/wiki/Trident_(%E6%8E%92%E7%89%88%E5%BC%95%E6%93%8E))
+ [Chrome](https://zh.wikipedia.org/wiki/Google_Chrome)：[Blink](https://zh.wikipedia.org/wiki/Blink)（衍生自 Webkit，使用在 Chrome v28 以上）、[Webkit](https://zh.wikipedia.org/wiki/WebKit)（使用在 Chrome v27 以下）
+ [Safari](https://zh.wikipedia.org/wiki/Safari)：[Webkit](https://zh.wikipedia.org/wiki/WebKit)
+ [Firefox](https://zh.wikipedia.org/wiki/Firefox)：[Gecko](https://zh.wikipedia.org/wiki/Gecko)

由此可知，為何網頁開發者都要針對不同的瀏覽器做排版樣式上的調整，以達到在各種不同瀏覽器下都能獲得共同的瀏覽體驗，其原因就在於這些瀏覽器採用不同的排版引擎，因此在解讀 HTML 文件或 CSS 樣式表時都會產生細微的差異，以致於造成跑版或破版的現象發生。

## 認識 HTML

好不容易，我們的電腦總算可以從遠端主機取得 HTML 文件，交給瀏覽器解讀且產生成我們易於閱讀的文件，接下來我們就要來認識怎麼撰寫瀏覽器看得懂的文件。

瀏覽器解讀的文件是採用「[超文件標示語言（HyperText Markup Language, HTML）](https://zh.wikipedia.org/wiki/HTML)」，運用一種「[超文字（hypertext）](https://zh.wikipedia.org/wiki/%E8%B6%85%E6%96%87%E6%9C%AC)」的設計概念，來讓文件與文件間可以產生關連，最簡單的案例就是我們在網頁裡看到的「連結」，點按連結之後就可以跳到其他頁面去，這就是 `hypertext` 了。

然而，我們該可以在 HTML 文件使用哪些標記元素？該怎麼寫？這些都由[全球資訊網協會（World Wide Web Consortium, W3C）](https://zh.wikipedia.org/wiki/%E4%B8%87%E7%BB%B4%E7%BD%91%E8%81%94%E7%9B%9F)制定標準，目前最新的修訂版本是 [HTML5](https://zh.wikipedia.org/wiki/HTML5)（並預計在 2016 年底發佈 HTML 5.1），目標是取代現行的 HTML 4.01 及 [XHTML](https://zh.wikipedia.org/wiki/XHTML) 1.0 標準。

如果你想知道瀏覽器與相關技術的發展史，你可以瀏覽「[網路演進](http://www.evolutionoftheweb.com/?hl=zh+tw#explore)」及「[網站技術發展史](http://www.openfoundry.org/tw/foss+forum/8917+2013+02+01+01+59+58)」等文章，相信可對 HTML 的標準制定與技術發展更瞭解。

值得注意的是，有時你會發現 HTML5 或 CSS3 標準內沒有制定的技術，在部分瀏覽器上還是可以實作，這是因為[網際網路標準通常是業界先行，等到業界發展出來的技術成為業界標準或實質標準時，也就是「大家都認同的技術」後，才會寫進標準規範中](https://www.microsoft.com/taiwan/technet/columns/profwin/40+wintcpip2.mspx)，所以在網路圈打混，得要具備自學能力，一直吸收網路圈的新知，這樣才能與時俱進。

### HTML 元素

要能夠開發、編寫網頁內容，就一定要熟知 HTML 元素，並瞭解各種 HTML 元素的用法。在開始下面章節前，建議你應該先瀏覽下「[HTML 元素](https://developer.mozilla.org/zh+TW/docs/Web/HTML/Element)」的頁面，以對 HTML 元素有初步的瞭解，同時也注意下哪些元素是只適用在 HTML5，而哪些元素又只適用在 HTML4。還有，因為 HTML 文件開發的前提應該是要適用於各種瀏覽器，所以也[應避免使用過時的語法](https://developer.mozilla.org/zh-TW/docs/Web_%E9%96%8B%E7%99%BC/Historical_artifacts_to_avoid)，以維持 HTML 文件的可讀性。

### 有效的 HTML 文件的結構

```html
<!DOCTYPE html>
<html>
  <head>
    <title>文件標題</title>
  </head>
  <body>
    <!-- 將你的網頁內容寫在這裡 -->
  </body>
</html>
```

1. `<!DOCTYPE>`：告知瀏覽器這份文件是使用哪個 HTML 版本所撰寫。https://developer.mozilla.org/zh+TW/docs/Glossary/Doctype
2. `<html>`：HTML 文件的主要(root)元素，每個 HTML 文件都必須有此元素，其他元素則必須被包含在這個元素之下。每個 HTML 文件只能有一個 `<html>` 元素。https://developer.mozilla.org/zh+CN/docs/Web/HTML/Element/html
3. `<head>`：定義 HTML 文件[後設資料（meta data）](https://zh.wikipedia.org/wiki/%E5%85%83%E6%95%B0%E6%8D%AE)的元素，包括文件的標題、CSS 樣式表及 JavaScript 腳本程式，以及提供給搜尋引擎或社交媒體網站辨識的描述資訊。每個 HTML 文件只能有一個 `<head>` 元素。https://developer.mozilla.org/zh+CN/docs/Web/HTML/Element/head
4. `<title>`：定義 HTML 文件標題的元素，這裡的標題會出現在瀏覽器的頁籤上；請注意，這裡的標題不會出現在瀏覽器的內容區。https://developer.mozilla.org/zh+CN/docs/Web/HTML/Element/title
5. `<body>`：用來包含 HTML 文件的主要內容，也是呈現在瀏覽器內容區的主要資訊來源。每個 HTML 文件只能有一個 `<body>` 元素。https://developer.mozilla.org/zh+CN/docs/Web/HTML/Element/body
6. `<!-- -->`：用來定義 HTML 文件中的註解內容，瀏覽器會忽略註解內容，只有在「檢視原始碼」的狀態下才會看到，主要是提供給網頁開發人員維護用的資訊。https://developer.mozilla.org/en+US/docs/Web/Guide/HTML/The_Importance_of_Correct_HTML_Commenting

一份格式正確的 HTML 文件，大體上都會包含以上說明的 HTML 元素（網頁註解則視需求而定），也就算得上是「有效的 HTML 文件」（valid HTML document）；如果你想要進一步瞭解何謂有效的 HTML 文件，或是想檢驗你所撰寫的 HTML 文件是否符合有效文件，你可以利用 [W3C 標記檢驗服務](https://developer.mozilla.org/en+US/docs/Web/Guide/HTML/The_Importance_of_Correct_HTML_Commenting)進行檢驗，以瞭解怎麼改善你的 HTML 文件使其符合有效文件。

### HTML 文件的語系標記法

我們可以在 `<html>` 元素加上 `lang` 的屬性，並標記該份 HTML 文件採用的語言為何。

```html
<html lang="zh-Hant">
<!--
zh-Hans 簡體中文
zh-Hans-CN 大陸地區使用的簡體中文
zh-Hans-HK 香港地區使用的簡體中文
zh-Hans-MO 澳門使用的簡體中文
zh-Hans-SG 新加坡使用的簡體中文
zh-Hans-TW 臺灣使用的簡體中文
zh-Hant 繁體中文
zh-Hant-CN 大陸地區使用的繁體中文
zh-Hant-HK 香港地區使用的繁體中文
zh-Hant-MO 澳門使用的繁體中文
zh-Hant-SG 新加坡使用的繁體中文
zh-Hant-TW 臺灣使用的繁體中文
-->
```

### HTML 文件的後設資料標記法

在上面的段落中有提到 `<head>` 元素會用來標記 HTML 文件的標題及後設資料，除此之外，通常也會標示該份文件的編碼方式。這些後設資料都是使用 `<meta>` 元素來定義的。

```html
<head>
  <!-- 定義字元編碼方式（僅適用 HTML5) -->
  <meta charset="utf-8">

  <!-- 定義字元編碼方式（僅適用 HTML4） -->
  <!-- 注意：下面這行在 HTML5 是不合法的用法 -->
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8">

  <!-- 三秒後重導向到別的頁面 -->
  <meta http-equiv="refresh" content="3;url=http://www.mozilla.org/">

  <!-- Google 搜尋引擎可以識別的中繼標記 -->
  <!-- 詳細說明請看 https://support.google.com/webmasters/answer/79812?hl=zh-Hant -->
  <meta name="description" content="我們可以在 HTML 的 Head 標記內寫入關於這個頁面的描述資訊">
  <meta name="google-site-verification" content="+nxGUDJ4QpAZ5l9Bsjdi102tLVC21AIh5d1Nl23908vVuFHs34="/>
  <meta name="robots" content="noindex,nofollow">
  <meta name="googlebot" content="noidex,nofollow" />
  <title>Meta 資訊的說明</title>

  <!-- Facebook 可以識別的中繼標記 -->
  <!-- 詳細說明請看 https://developers.facebook.com/docs/sharing/webmasters#markup -->
  <meta property="og:title" content="文章標題"/>
  <meta property="og:image" content="https://davidwalsh.name/wp-content/themes/klass/img/facebooklogo.png"/>
  <meta property="og:site_name" content="網站名稱"/>
  <meta property="og:description" content="我們可以在 HTML 的 Head 標記內寫入關於這個頁面的描述資訊">

  <!-- Twitter 可以識別的中繼標記 -->
  <!-- 詳細說明請看 https://dev.twitter.com/cards/markup -->
  <meta name="twitter:card" content="summary" />
  <meta name="twitter:description" content="The table in this section explains Twitter Card elements and any Open Graph protocol markup fallbacks." />
  <meta name="twitter:title" content="Cards Markup Tag Reference" />
  <meta name="twitter:image" content="https://pbs.twimg.com/profile_images/2284174872/7df3h38zabcvjylnyfe3.png" />
</head>
```

除了 `<meta>` 元素定義後設資料外，我們也會使用 `<link>` 元素來引用外部 CSS 樣式表，以及使用 `<script>` 元素來引用外部的 JavaScript 腳本程式。

```html
<head>
  <link rel="stylesheet" type="text/css" href="styles.css">
  <script src="scripts.js"></script>
</head>
```

### HTML 文件的編碼方式

有時候我們在瀏覽網頁時會看到「亂碼」，通常都是因為[瀏覽器的字元編碼](https://zh.wikipedia.org/wiki/HTML%E5%AD%97%E7%AC%A6%E7%BC%96%E7%A0%81)設定錯誤的問題。由於電腦只能儲存 0 與 1 兩種狀態，所以電腦之間的資料交換都必須先將資料轉換成 0/1 型式的內容，例如說我想要傳送「`A`」給對方的電腦，但我怎麼知道要將 `A` 轉換成什麼數字呢？這個問題就要靠[字元編碼](https://zh.wikipedia.org/wiki/%E5%AD%97%E7%AC%A6%E7%BC%96%E7%A0%81)來解決，字元編碼是電腦之間用來溝通的一套符號集，以剛剛的例子來說，我們必須先將 `A` 轉換成一個「數字」，然後傳送給對方的電腦，而對方的電腦取得這個「數字」時，也要能夠知道轉換回 `A`。就像「摩斯電碼」一樣，使用摩斯電腦交換資訊的兩方，都要有一本轉譯本，才能將接受到的資訊轉譯回真實的資料內容。

如果我們只是要交換「英文」資料，那事情就簡單很多，因為電腦在很早期就已經發展出「[ASCII（American Standard Code for Information Interchange，美國資訊交換標準代碼）](https://zh.wikipedia.org/zh-tw/ASCII)，就例如剛剛提到的 `A` 會先轉譯成 `65`（也就是二進位的 `01000001`），然後將這一串二進位資料型式的內容傳送給對方，對方電腦收到這串二進位資料型式的內容後，會去對照 ASCII 表，查到這串資料其實就是指 `A`，因此要順利完成進行資料交換的話，首要條件是雙方都使用同一套編碼方式。

講到這裡，應該就會知道為什麼在瀏覽網頁時會看到「亂碼」了吧，其實亂碼的出現就是因為資料交換的兩方不是採用同一套編碼方式，以致於無法呈現正確的資料內容。那麼為什麼有時我們明明在網頁內容寫的是中文，也都正確的顯示，但透過瀏覽器顯示時又會造成亂碼呢？這是段[很久遠的歷史故事](http://python.ez2learn.com/basic/unicode.html)了，總之大部分都可能是因為網頁儲存成 [Big5](https://zh.wikipedia.org/zh-hant/%E5%A4%A7%E4%BA%94%E7%A2%BC) 編碼方式，而瀏覽器是設定成 [UTF-8](https://zh.wikipedia.org/wiki/UTF-8) 的編碼方式，以致於無法正確顯示中文。

所以，如果你也遇到「亂碼」，那你可以先確認一下網頁的編碼方式是 `utf-8` 還是 `big5`。由於某些歷史緣故，建議直接採用 `utf-8` 編碼方式，不只可以正確中文，也可以正確顯示其他語言的文字。

```html
<meta charset="utf-8">
```

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
