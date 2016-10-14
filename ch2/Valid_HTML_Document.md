# 有效的 HTML 文件的結構

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

## HTML 文件的語系標記法

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

## HTML 文件的後設資料標記法

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

## HTML 文件的編碼方式

有時候我們在瀏覽網頁時會看到「亂碼」，通常都是因為[瀏覽器的字元編碼](https://zh.wikipedia.org/wiki/HTML%E5%AD%97%E7%AC%A6%E7%BC%96%E7%A0%81)設定錯誤的問題。由於電腦只能儲存 0 與 1 兩種狀態，所以電腦之間的資料交換都必須先將資料轉換成 0/1 型式的內容，例如說我想要傳送「`A`」給對方的電腦，但我怎麼知道要將 `A` 轉換成什麼數字呢？這個問題就要靠[字元編碼](https://zh.wikipedia.org/wiki/%E5%AD%97%E7%AC%A6%E7%BC%96%E7%A0%81)來解決，字元編碼是電腦之間用來溝通的一套符號集，以剛剛的例子來說，我們必須先將 `A` 轉換成一個「數字」，然後傳送給對方的電腦，而對方的電腦取得這個「數字」時，也要能夠知道轉換回 `A`。就像「摩斯電碼」一樣，使用摩斯電腦交換資訊的兩方，都要有一本轉譯本，才能將接受到的資訊轉譯回真實的資料內容。

如果我們只是要交換「英文」資料，那事情就簡單很多，因為電腦在很早期就已經發展出「[ASCII（American Standard Code for Information Interchange，美國資訊交換標準代碼）](https://zh.wikipedia.org/zh-tw/ASCII)，就例如剛剛提到的 `A` 會先轉譯成 `65`（也就是二進位的 `01000001`），然後將這一串二進位資料型式的內容傳送給對方，對方電腦收到這串二進位資料型式的內容後，會去對照 ASCII 表，查到這串資料其實就是指 `A`，因此要順利完成進行資料交換的話，首要條件是雙方都使用同一套編碼方式。

講到這裡，應該就會知道為什麼在瀏覽網頁時會看到「亂碼」了吧，其實亂碼的出現就是因為資料交換的兩方不是採用同一套編碼方式，以致於無法呈現正確的資料內容。那麼為什麼有時我們明明在網頁內容寫的是中文，也都正確的顯示，但透過瀏覽器顯示時又會造成亂碼呢？這是段[很久遠的歷史故事](http://python.ez2learn.com/basic/unicode.html)了，總之大部分都可能是因為網頁儲存成 [Big5](https://zh.wikipedia.org/zh-hant/%E5%A4%A7%E4%BA%94%E7%A2%BC) 編碼方式，而瀏覽器是設定成 [UTF-8](https://zh.wikipedia.org/wiki/UTF-8) 的編碼方式，以致於無法正確顯示中文。

所以，如果你也遇到「亂碼」，那你可以先確認一下網頁的編碼方式是 `utf-8` 還是 `big5`。由於某些歷史緣故，建議直接採用 `utf-8` 編碼方式，不只可以正確中文，也可以正確顯示其他語言的文字。

```html
<meta charset="utf-8">
```