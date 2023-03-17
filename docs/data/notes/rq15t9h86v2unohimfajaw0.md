
## 1. 圖片 RWD 與不變形和壓縮

### 1.1. 在網頁上的圖片格式

- JPEG（.jpg）：這是最常見的圖片格式之一，通常用於照片和圖片，因為它可以壓縮圖像以減小文件大小，同時保持高品質的圖像。JPEG 格式的圖像可以包含 1600 萬個顏色，這使得它成為展示高品質照片的理想格式。

- PNG（.png）：PNG 格式的圖像通常用於圖形和圖像，因為它可以支持透明背景。PNG 格式的圖像不會有品質損失，因此它可以用於需要高品質圖像的場合。

- GIF（.gif）：GIF 格式的圖像通常用於動畫，因為它可以包含多個圖像幀。GIF 格式的圖像可以包含最多 256 種顏色，這使得它不適合展示高品質照片，但非常適合用於簡單的圖形和動畫。

- SVG（.svg）：SVG 格式的圖像是矢量圖形，它們可以縮放到任何大小而不會失去品質。SVG 格式的圖像通常用於圖形和圖像，特別是需要在不同尺寸的屏幕上顯示的場合。

- WebP（.webp）：WebP 格式的圖像是由 Google 開發的一種圖像格式，它可以壓縮圖像以減小文件大小，同時保持高品質的圖像。WebP 格式的圖像通常用於網頁，因為它們可以加快網頁加載速度。

- AVIF（.avif）： 是一種現代的圖像格式，它是基於開放標準的編碼方式，可提供更高的圖像品質和更小的文件大小。AVIF 格式通常用於網頁、移動應用程序和其他需要高質量圖像的應用程序。

## 2. HTML 圖片的載入(像素密度、螢幕寬度、多種格式)

`srcset` 屬於 HTML 中 `<img>` 或 `<source>` 標籤的屬性，可用於指定可替代圖片的多種版本，並讓瀏覽器根據不同的設備和網路環境自動選擇最適合的圖片版本載入。srcset 屬性支援的圖片格式包括 `PNG`、`JPEG`、`WebP`、`AVIF` 等。常見的用法有以下幾種：

### 2.1. HTML `<img>` 和 `<source>` 的屬性

- `srcset`、`sizes` 屬於 HTML 中 `<img>` 或 `<source>` 標籤的屬性。

  - `<img>` 內使用方式：

  ```html
  <img
    srcset="
      /img/html/vangogh-sm.jpg 120w,
      /img/html/vangogh.jpg    193w,
      /img/html/vangogh-lg.jpg 278w
    "
    sizes="(max-width: 710px) 120px,
              (max-width: 991px) 193px,
              278px"
    loading="lazy"
  />
  ```

  > `<img>` 可以設定 `loading="lazy"` 來延遲載入圖片。
  > 這樣會載入一張圖片，首次載入頁面瀏覽器會根據 `srcset` 判斷要顯示哪張圖，之後用 `sizes` 判斷要顯示哪個尺寸。

  - `<source>` 內使用方式 ：

  ```html
  <picture>
    <source
      srcset="
        /img/html/vangogh-sm.jpg 120w,
        /img/html/vangogh.jpg    193w,
        /img/html/vangogh-lg.jpg 278w
      "
      sizes="(max-width: 710px) 120px,
             (max-width: 991px) 193px,
             278px"
    />
    <img
      src="/img/html/vangogh-lg.jpg"
      alt="Vincent Van Gogh"
    />
  </picture>
  ```

  - `srcset` 代表：

    圖片寬度 120w 時用 vangogh-sm.jpg

    圖片寬度 193w 時用 vangogh.jpg

    圖片寬度 278w 時用 vangogh-lg.jpg

  - `sizes` 代表，可以用來設定圖片大小：

    在寬度在 0 到 710px 的螢幕上，圖片寬度為 120px。

    在寬度在 711px 到 991px 的螢幕上，圖片寬度為 193px。

    在寬度為 992px 及以上的螢幕上，圖片寬度為 278px。

使用方式：

- `<tagname srcset="URL width(圖片寬度)">`
- `<tagname sizes="(media-condition) width(圖片寬度)">`

來源： [HTML srcset Attribute](https://www.dofactory.com/html/srcset)

### 2.2. 指定不同像素密度的圖片版本

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

srcset 中的 1x、2x、3x 等是相對于 DPR（Device Pixel Ratio，設備像素比）而言的，而 DPR 是指設備的物理像素數與邏輯像素數（CSS 像素數）之間的比率。

所以 srcset 的 1x、2x、3x 等可以被視為基於 DPR 的分辨率倍數。

而 PPI 則是指每英寸的像素數量，通常用來描述螢幕或打印品的像素密度。兩者是不同的概念。

DPR 指的是圖片寬度和 `viewport` 寬度之比，計算方式如下：(圖片寬度) / (`viewport` 寬度)

```
orig.jpg：DPR = 600/600 = 1
wider.jpg：DPR = 1200/600 = 2
widest.jpg：DPR = 2000/600 = 3.33
```

參考自： [Understanding the Device Pixel Ratio](https://tomroth.com.au/dpr/)

![](/assets/images/2023-03-12-23-26-43.png)

> google devtool 可以開啟 DPR (Device Pixel Ratio)，預設為 DPR 2，如果你 srcset 有用 1.5x 但沒 2x，裝置會從預設的往下找最高的圖來用，所以會顯示 1.5x 的那張圖。

圖片網址： [Responsive images - try it](https://googlesamples.github.io/web-fundamentals/fundamentals/design-and-ux/responsive/sizes.html)

參考： [How to simulate pixel ratio to test media queries with Google Chrome or Firefox on Windows? - stackoverflow](https://stackoverflow.com/questions/16382542/how-to-simulate-pixel-ratio-to-test-media-queries-with-google-chrome-or-firefox)

### 2.3. 指定不同螢幕寬度的圖片版本

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

在 `srcset` 中，`w` 是一種描述圖像大小的單位，代表圖像的寬度，`1w = 1px`。

它用來告訴瀏覽器圖像的像素密度，讓瀏覽器可以選擇最適合當前設備的圖像大小。

例如，`320w` 意味著圖像的寬度為 `320 像素`。

以上範例適用於 `width: 100%` 圖片。

### 2.4. 指定多種格式的圖片版本

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

參考： [Responsive images - web.dev](https://web.dev/responsive-images/#art-direction-in-responsive-images-with-picture)

## 3. 混用

`w` 和 `x` 可以混用。

```html
<img
  alt="my awesome image"
  src="banner.jpeg"
  srcset="banner-HD.jpeg 2x, banner-phone.jpeg 640w, banner-phone-HD.jpeg 640w 2x"
/>
```

參考自： [High DPI images for variable pixel densities - web.dev](https://web.dev/high-dpi/)

## 4. 圖片解析度? DPI、PPI、LPI?

### 4.1. LPI 和 DPI 通常用來描述印刷品的解析度和清晰度

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

### 4.2. PPI 圖像的解析度

- PPI (Pixels per inch)：為每英吋多少像素，通 q 常是指圖像的解析度。假如一個印刷品圖像為 300 PPI，代表其每英寸有 300 像素，PPI 數值越高，檔案越大，螢幕顯示的圖像越精細；相反地 PPI 越低，檔案越小，圖片越不清楚。

螢幕的像素密度可按以下公式計算：
`像素密度 = (總像素數的平方根) / 對角線尺寸`

27 吋 720P 螢幕 PPI 約為 54.78 PPI。
27 吋 1080P 螢幕 PPI 約為 82.1 PPI。
27 吋 4K 螢幕 PPI 約為 163.18 PPI。
27 吋 8K 螢幕 PPI 約為 326 ppi 左右。 (ChatGPT 計算結果)

關於 PPI 根據 [ios-resolution](https://www.ios-resolution.com/)

iphone 最高畫質為 476 PPI，ipad 最高畫質為 326 PPI。

## 5. CSS 設定 DPR 與 DPI media query

在 CSS 中，可以使用媒體查詢（media queries）的方式，根據設備的像素密度（DPR）指定相應的圖像資源。例如：

```css
@media (-webkit-min-device-pixel-ratio: 2),
  (min-resolution: 192dpi) {
  /* 這裡是2x圖片的樣式 */
  background-image: url(image@2x.png);
}
```

> - [resolution - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/resolution)
> - [-webkit-device-pixel-rate（非標準盡量別用) - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/resolution)

在這個例子中，如果設備的像素密度是 2，

或者顯示器的分辨率達到了 192dpi（每英寸點數）以上，就會顯示 image@2x.png。

注意，不同的設備可能使用不同的查詢方式，上面的例子只是其中一種。

## 6. 使用 sharp 來將 svg 轉檔

![](/assets/images/2023-03-12-22-58-31.png)

以圖片轉檔工具 [sharp](https://sharp.pixelplumbing.com/api-constructor) 為例，TIFF 和 PDF 才可以用 `sharp` 設定 DPI。

其他格式如 `avif`、`webp`、`jpeg`、`png` 沒辦法用這個設定，產出來的圖都會是 72 ppi，所以如果是用 `svg` 原始 `320px` 寬的要轉圖給 srcset 2x 用，要設定成產生寬 `640px` 的圖，就可以達到兩倍 PPI `320:640(px) = 1:2(DPR) = 72:144(PPI)` 的效果。(注意： 因為 svg 是向量圖，所以可以這樣無損產生比較大尺寸的圖，若是點陣圖要產新尺寸，只能往下不然會變模糊。)

附註： [可以下載吳哲宇大大用 sharp 寫好的 js 來用](https://github.com/frank890417/image-optimizer)

- 所以可以這樣用 (以下共有三張圖稿，需要各產五種圖檔)：

```html
<picture>
  <source
    srcset="
      /assets/images/tutor/tutor_LG/tutor_LG-1170.avif,
      /assets/images/tutor/tutor_LG/tutor_LG-1.5x.avif 1.5x
    "
    media="(min-width: 1170px)"
    type="image/avif"
  />
  <source
    srcset="
      /assets/images/tutor/tutor_LG/tutor_LG-1170.webp,
      /assets/images/tutor/tutor_LG/tutor_LG-1.5x.webp 1.5x
    "
    media="(min-width: 1170px)"
    type="image/webp"
  />
  <source
    srcset="
      /assets/images/tutor/tutor_LG/tutor_LG-1170.jpeg
    "
    media="(min-width: 1170px)"
    type="image/jpeg"
  />
  <source
    srcset="
      /assets/images/tutor/tutor_MD/tutor_MD-768.avif,
      /assets/images/tutor/tutor_MD/tutor_MD-1.5x.avif 1.5x
    "
    media="(min-width: 768px)"
    type="image/avif"
  />
  <source
    srcset="
      /assets/images/tutor/tutor_MD/tutor_MD-768.webp,
      /assets/images/tutor/tutor_MD/tutor_MD-1.5x.webp 1.5x
    "
    media="(min-width: 768px)"
    type="image/webp"
  />
  <source
    srcset="
      /assets/images/tutor/tutor_MD/tutor_MD-768.jpeg
    "
    media="(min-width: 768px)"
    type="image/jpeg"
  />
  <source
    srcset="
      /assets/images/tutor/tutor_SM/tutor_SM-320.avif,
      /assets/images/tutor/tutor_SM/tutor_SM-1.5x.avif 1.5x
    "
    media="(min-width: 320px)"
    type="image/avif"
  />
  <source
    srcset="
      /assets/images/tutor/tutor_SM/tutor_SM-320.webp,
      /assets/images/tutor/tutor_SM/tutor_SM-1.5x.webp 1.5x
    "
    media="(min-width: 320px)"
    type="image/webp"
  />
  <source
    srcset="
      /assets/images/tutor/tutor_SM/tutor_SM-320.jpeg
    "
    media="(min-width: 320px)"
    type="image/jpeg"
  />
  <img
    alt="tutor image"
    sizes="(max-width: 767px) 320px,
                (max-width: 1169px) 768px,
                1170px"
    srcset="
      /assets/images/tutor/tutor_SM/tutor_SM-320.jpeg   320w,
      /assets/images/tutor/tutor_MD/tutor_MD-768.jpeg   768w,
      /assets/images/tutor/tutor_LG/tutor_LG-1170.jpeg 1170w
    "
    loading="lazy"
  />
</picture>
```

- 圖片用 svg 產生以下尺寸：

![](/assets/images/2023-03-13-00-45-19.png)

## 小結

- 以後就知道圖片可以跟設計師要 `svg` 轉檔會最方便。

不然就要直接跟對方要最大尺寸的 `jpeg` 圖片。(72ppi，如果是要 1170px 寬的，就要跟他要個 1.5 倍或 2 倍大小的圖，這樣才能往下縮小並產生對應的檔案類型)。

點陣圖要 `jpeg` 檔案會比較省空間。（用了 `sharp` 才發現 `png` 會比 `jpeg` 大）。

另外轉 `avif` 和 `webp` 就交給 `sharp`。

- `img` 的 `srcset` 一次只會載入一張圖。如果要畫面伸縮時根據寬度更新成另一張圖檔，要使用 `source` 的 `media` 或使用 css 的 `media query`。

如下，不管畫面伸縮成何尺寸，都只會載入第一次載入畫面的那一張圖檔，但伸縮畫面時這張圖會根據 `sizes` 顯示指定尺寸。

```html
<img
  alt="tutor image"
  sizes="(max-width: 767px) 320px,
                (max-width: 1169px) 768px,
                1170px"
  srcset="
    /assets/images/tutor/tutor_SM/tutor_SM-320.jpeg   320w,
    /assets/images/tutor/tutor_MD/tutor_MD-768.jpeg   768w,
    /assets/images/tutor/tutor_LG/tutor_LG-1170.jpeg 1170w
  "
  loading="lazy"
/>
```

> 如果要伸縮時動態更新圖檔，要使用 `source` 的 `media` 屬性或使用 css 的 `media query` 。

## IIS 設定 MIME 類型

如果 IIS 沒有該類型要記得去設定，不然 server 會誤以為 avif 和 webp 是 `text/html` 而無法顯示。

- [How to add a MIME type to a Web site or application - Microsoft](https://learn.microsoft.com/en-us/iis/configuration/system.webserver/staticcontent/mimemap)

- [How to Serve AVIF Image on IIS](https://www.itnota.com/serving-avif-image-iis/)
