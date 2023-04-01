
## 網頁的可用性和可讀性

當設計網頁或應用程式時，使用適當的顏色和對比度可以幫助提高可用性和可讀性，尤其對視力受損的使用者更加重要。

W3C 所提出的 Web Content Accessibility Guidelines (WCAG) 定義了三個級別的要求，

分別是 A、AA 和 AAA 級，針對顏色和對比度的要求如下：

* WCAG A 級

所有非純裝飾的文本（例如，段落和標題）必須有足夠的對比度，以便在正常閱讀條件下閱讀。
對比度應達到至少 `4.5:1`，對於大型文本（大於14pt或加粗16pt）應達到至少 `3:1`。

* WCAG AA 級

所有文本必須符合WCAG A級的要求。
對比度應達到至少 `4.5:1`，對於大型文本（大於14pt或加粗16pt）應達到至少 `3:1`。
預錄的音訊和視訊媒體必須有文字備註，以幫助視力障礙使用者了解其內容。

* WCAG AAA 級

所有文本必須符合 WCAG AA 級的要求。
對比度應達到至少 `7:1`，對於大型文本（大於14pt或加粗16pt）應達到至少 `4.5:1`。
所有視訊媒體必須有閱讀傳譯，以幫助聽力障礙使用者了解其內容。
需要提供其他輔助功能，例如語音控制、鍵盤操作等，以提高可用性。

## W3C 測試與評估

[測試與評估 - W3C](https://www.w3.org/WAI/test-evaluate/preliminary/)

* 簡單檢查 - 第一次審查 (Easy Checks - A First Review)
* [評估工具 (Evaluation Tools)](https://www.w3.org/WAI/ER/tools/)
* 一致性評估、報告 (Conformance Evaluation, Reports)
* 結合專業知識 (Using Combined Expertise)
* 涉及使用者 (Involving Users)

雖然 w3c [Keyboard access and visual focus](https://www.w3.org/WAI/demos/bad/after/survey) 的地方做得很好，但 w3c 的網站沒有到 google lighthouse 100 xD
![](/assets/images/2023-04-01-22-13-26.png)

## a11y (accessibility)

以上規範都是為了可用性 (a11y) 這邊有關於是障朋友如何使用網頁的影片。

[視障者使用網頁閱讀軟體](https://www.youtube.com/watch?v=dEbl5jvLKGQ)

來源: [Accessibility For Websites (A11y)](https://onward.justia.com/accessibility-for-websites-a11y/)

螢幕閱讀器可以下載這套 google 推薦的免費軟體 [NVDA](https://www.nvaccess.org/download/) 來用。

## 小結

A11y 得分高，通常 google SEO 也會不低。

但如果要有精美 UI 又要針對視障或聽障朋友開發網頁還蠻難的。因為同樣工作時間內要做比較多事。

按 tab 可以閱讀所有連結和文字內容可參考: [中華民國總統府網頁](https://www.president.gov.tw/)

![](/assets/images/2023-04-01-23-17-53.png)

> 但 A11y 分數不高阿...

![](/assets/images/2023-04-01-23-35-01.png)

> 白宮的 100 分，而且按 tab 可以瀏覽到所有地方! 以後要做 a11y 絕對首先參考白宮，哈哈。

以開發角度來看用 tab 鍵切換區塊，tab 是照著 html 的順序去讀的，一開始設計畫面就要想好 tab 的移動方向，然後工程師開發的同時也要檢查，同時也要用 Lighthouse 做檢查xD。更進階的話，要找使用者來測試並根據問題做調整。
