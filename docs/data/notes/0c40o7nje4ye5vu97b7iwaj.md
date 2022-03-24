
因為設計稿給了三種尺寸 pc/pad/phone，

然後程式裡有三個用 min-width 分開的中斷點 1170px/768px/320px

(所以中斷點吃不到的地方就吃預設值)

``` javascript
┌──────────────────┐
│ 320  768   1170  │
│  │→   │→     │→  │
└──────────────────┘
```

一開始想說應該是到中斷點就換版型的排版，結果好像是 pad(768px) 以下要變流動(Liquid)的排版。

機會難得想把這篇文章的東西英翻中，記錄一下xD (文章作者是:Steven Bradley)

https://vanseodesign.com/web-design/fixed-or-liquid-design/
