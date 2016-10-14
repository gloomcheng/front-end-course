# 排版引擎（Layout Engine）

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