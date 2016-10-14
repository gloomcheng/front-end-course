# 統一資源定位符 (Uniform Resource Locator, URL)

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