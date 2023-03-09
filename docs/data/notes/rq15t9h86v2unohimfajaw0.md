
## 1. 圖片 RWD 與不變形和壓縮

### 1.1. 在網頁上的圖片格式

- JPEG（.jpg）：這是最常見的圖片格式之一，通常用於照片和圖片，因為它可以壓縮圖像以減小文件大小，同時保持高品質的圖像。JPEG 格式的圖像可以包含 1600 萬個顏色，這使得它成為展示高品質照片的理想格式。

- PNG（.png）：PNG 格式的圖像通常用於圖形和圖像，因為它可以支持透明背景。PNG 格式的圖像不會有品質損失，因此它可以用於需要高品質圖像的場合。

- GIF（.gif）：GIF 格式的圖像通常用於動畫，因為它可以包含多個圖像幀。GIF 格式的圖像可以包含最多 256 種顏色，這使得它不適合展示高品質照片，但非常適合用於簡單的圖形和動畫。

- SVG（.svg）：SVG 格式的圖像是矢量圖形，它們可以縮放到任何大小而不會失去品質。SVG 格式的圖像通常用於圖形和圖像，特別是需要在不同尺寸的屏幕上顯示的場合。

- WebP（.webp）：WebP 格式的圖像是由 Google 開發的一種圖像格式，它可以壓縮圖像以減小文件大小，同時保持高品質的圖像。WebP 格式的圖像通常用於網頁，因為它們可以加快網頁加載速度。

- AVIF（.avif）： 是一種現代的圖像格式，它是基於開放標準的編碼方式，可提供更高的圖像品質和更小的文件大小。AVIF 格式通常用於網頁、移動應用程序和其他需要高質量圖像的應用程序。

## 2. HTML 圖片的載入(像素密度、螢幕寬度、多種格式)

srcset 屬於 HTML 中 `<img>` 或 `<source>` 標籤的屬性，可用於指定可替代圖片的多種版本，並讓瀏覽器根據不同的設備和網路環境自動選擇最適合的圖片版本載入。srcset 屬性支援的圖片格式包括 PNG、JPEG、WebP、AVIF 等。常見的用法有以下幾種：

### 2.1. 指定不同像素密度的圖片版本

```html
<img
  srcset="
    image-1x.png 1x,
    image-2x.png 2x,
    image-3x.png 3x
  "
  src="image-1x.png"
  alt="..."
/>
```

例如，如果當前設備的像素密度為 2x，則會載入 image-2x.png 這個版本的圖片。

### 2.2. 指定不同螢幕寬度的圖片版本

```html
<img
  srcset="
    image-320w.png 320w,
    image-480w.png 480w,
    image-640w.png 640w,
    image-960w.png 960w
  "
  src="image-320w.png"
  alt="..."
/>
```

例如，如果當前設備的螢幕寬度為 500px，則會載入 image-480w.png 這個版本的圖片。

在 `srcset` 中，`w` 是一種描述圖像大小的單位，代表圖像的寬度。

它用來告訴瀏覽器圖像的像素密度，讓瀏覽器可以選擇最適合當前設備的圖像大小。

例如，`320w` 意味著圖像的寬度為 `320 像素`。

### 2.3. 指定多種格式的圖片版本

```html
<picture>
  <!-- 有支援的話，會先載入 -->
  <source
    srcset="
      /img/my-picture.avif
    "
    type="image/avif"
  />
  <!-- 否則次載入 -->
  <source
    srcset="
      /img/my-picture.webp
    "
    type="image/webp"
  />
  <!-- 以上都不支援，則載入 -->
  <img
    src="/img/my-picture.jpg"
    loading="lazy"
    alt="my-picture"
  />
</picture>
```

這個圖片使用了 `<picture>` 元素，並在其中嵌套了 `<source>` 和 `<img>` 元素。當瀏覽器加載圖片時，它會首先從 `<source>` 中選擇符合條件的圖像，如果沒有符合條件的，則會載入 `<img>` 中指定的圖片。

## 3. 圖片解析度? DPI、PPI、LPI?

### 3.1. LPI 和 DPI 通常用來描述印刷品的解析度和清晰度

- DPI (Dot per inch)：為每英吋多少點，DPI 是用來描述數位影像解析度的單位，通常用於電腦顯示器或數位印刷上。

- LPI (Lines per inch)：為每英吋多少印刷網線，業界常提到的網線數、條數就是 LPI，由點構成線為單位。

高階印刷機規格以 2400 DPI 為主， 1200 DPI 低階印刷機及 600 DPI 家用印表機。

它們的關係是：`DPI ≥ 2 x LPI`，也就是說，DPI 至少應該是 LPI 的兩倍才能保證能夠呈現出平滑的圖像。

因此，如果要達到 300 LPI 的效果，至少需要 600 DPI 的打印分辨率。

LPI 是指印刷時網點的線數，描述了印刷品上印刷網點的密度和大小；DPI 是指印刷時打印機頭上的噴墨或雷射打印頭的密度，描述了打印時可打印的最小點的大小。

**無版印刷**可以使用 DPI，例如數位噴墨印刷機或數位直接印刷機都需要指定 DPI 的設定。

**平版印刷**則通常使用 LPI，表示每英吋使用多少線網印刷，以及使用何種角度設定網點的大小。

因此，DPI 和 LPI 雖然都是描述解析度的單位，但是用途和應用場景不同。

![](/assets/images/2023-03-02-21-40-40.png)

> [高英工商自編教材](https://www.kyicvs.khc.edu.tw/images/ckfinder/books1/des03/mobile/index.html#p=47)

![](/assets/images/2023-03-02-21-43-48.png)

> [【印刷概論】01 正修科大](https://modern.csu.edu.tw/wSite/public/Attachment/f1398761171894.pdf)

![](/assets/images/2023-03-02-21-46-54.png)

> 無版印刷不需曬版製版階段。

![](/assets/images/2023-03-02-21-59-44.png)

> [恆成小學堂總複習：網點 / 線數 LPI（Lines Per Inch）](https://www.facebook.com/auspicpaper/posts/pfbid02HxYddX7dg42Z3i5xS5ZvzuYt8osE6ShYbM5yg3bwRgkXz2uz69X8Bved2NnrfK7jl)

### 3.2. PPI 圖像的解析度

- PPI (Pixels per inch)：為每英吋多少像素，通 q 常是指圖像的解析度。假如一個印刷品圖像為 300 PPI，代表其每英寸有 300 像素，PPI 數值越高，檔案越大，螢幕顯示的圖像越精細；相反地 PPI 越低，檔案越小，圖片越不清楚。

螢幕的像素密度可按以下公式計算：
`像素密度 = (總像素數的平方根) / 對角線尺寸`

27 吋 4K 螢幕 PPI 為 163.18 PPI。
27 吋 8K 螢幕 PPI 約為 326 ppi 左右。 (ChatGPT 計算結果)

關於 PPI 根據 [ios-resolution](https://www.ios-resolution.com/)

iphone 最高畫質為 476 PPI，ipad 最高畫質為 326 PPI。
