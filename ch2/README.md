# 認識 HTML

好不容易，我們的電腦總算可以從遠端主機取得 HTML 文件，交給瀏覽器解讀且產生成我們易於閱讀的文件，接下來我們就要來認識怎麼撰寫瀏覽器看得懂的文件。

瀏覽器解讀的文件是採用「[超文件標示語言（HyperText Markup Language, HTML）](https://zh.wikipedia.org/wiki/HTML)」，運用一種「[超文字（hypertext）](https://zh.wikipedia.org/wiki/%E8%B6%85%E6%96%87%E6%9C%AC)」的設計概念，來讓文件與文件間可以產生關連，最簡單的案例就是我們在網頁裡看到的「連結」，點按連結之後就可以跳到其他頁面去，這就是 `hypertext` 了。

然而，我們該可以在 HTML 文件使用哪些標記元素？該怎麼寫？這些都由[全球資訊網協會（World Wide Web Consortium, W3C）](https://zh.wikipedia.org/wiki/%E4%B8%87%E7%BB%B4%E7%BD%91%E8%81%94%E7%9B%9F)制定標準，目前最新的修訂版本是 [HTML5](https://zh.wikipedia.org/wiki/HTML5)（並預計在 2016 年底發佈 HTML 5.1），目標是取代現行的 HTML 4.01 及 [XHTML](https://zh.wikipedia.org/wiki/XHTML) 1.0 標準。

如果你想知道瀏覽器與相關技術的發展史，你可以瀏覽「[網路演進](http://www.evolutionoftheweb.com/?hl=zh+tw#explore)」及「[網站技術發展史](http://www.openfoundry.org/tw/foss+forum/8917+2013+02+01+01+59+58)」等文章，相信可對 HTML 的標準制定與技術發展更瞭解。

值得注意的是，有時你會發現 HTML5 或 CSS3 標準內沒有制定的技術，在部分瀏覽器上還是可以實作，這是因為[網際網路標準通常是業界先行，等到業界發展出來的技術成為業界標準或實質標準時，也就是「大家都認同的技術」後，才會寫進標準規範中](https://www.microsoft.com/taiwan/technet/columns/profwin/40+wintcpip2.mspx)，所以在網路圈打混，得要具備自學能力，一直吸收網路圈的新知，這樣才能與時俱進。