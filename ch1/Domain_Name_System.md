# 網域名稱系統（Domain Name System, DNS）

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