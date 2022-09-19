---
id: about
title: About
desc: ""
updated: 1663249615500
created: 1641017236114
---

嗨，我是 naomi。 這個部落格是用 Dendron 官方提供的樣板製作而成的。

紀錄工作上工作下的程式相關筆記。 關於筆記內容:

如果有時間會盡量翻譯原文，翻譯的地方會附上原文，因為自己不是專業的翻譯員，翻得不妥還有原文在。
基本上會附上參考與引用的出處。

<!-- [背景音樂✨](https://www.youtube.com/watch?v=GTlQhMRHXIg) -->

<div id="wrap">
    <div id="player"></div>
    <div id="btn-area">
        <button id="btn-stop" onclick="stopVideo()">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zM8 7a1 1 0 00-1 1v4a1 1 0 001 1h4a1 1 0 001-1V8a1 1 0 00-1-1H8z" clip-rule="evenodd"></path>
            </svg>
        </button>
        <button id="btn-play" onclick="playMyVedio()">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zM9.555 7.168A1 1 0 008 8v4a1 1 0 001.555.832l3-2a1 1 0 000-1.664l-3-2z" clip-rule="evenodd"></path>
            </svg>
        </button>
        <button id="btn-pause" onclick="pauseVideo()">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zM7 8a1 1 0 012 0v4a1 1 0 11-2 0V8zm5-1a1 1 0 00-1 1v4a1 1 0 102 0V8a1 1 0 00-1-1z" clip-rule="evenodd"></path>
        </svg>
        </button>
        <button id="btn-unMute" onclick="unMute()" style="display: none;">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M9.383 3.076A1 1 0 0110 4v12a1 1 0 01-1.707.707L4.586 13H2a1 1 0 01-1-1V8a1 1 0 011-1h2.586l3.707-3.707a1 1 0 011.09-.217zM12.293 7.293a1 1 0 011.414 0L15 8.586l1.293-1.293a1 1 0 111.414 1.414L16.414 10l1.293 1.293a1 1 0 01-1.414 1.414L15 11.414l-1.293 1.293a1 1 0 01-1.414-1.414L13.586 10l-1.293-1.293a1 1 0 010-1.414z" clip-rule="evenodd"></path>
        </svg>
        </button>
        <button id="btn-mute" onclick="mute()" style="display: flex;">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M9.383 3.076A1 1 0 0110 4v12a1 1 0 01-1.707.707L4.586 13H2a1 1 0 01-1-1V8a1 1 0 011-1h2.586l3.707-3.707a1 1 0 011.09-.217zM14.657 2.929a1 1 0 011.414 0A9.972 9.972 0 0119 10a9.972 9.972 0 01-2.929 7.071 1 1 0 01-1.414-1.414A7.971 7.971 0 0017 10c0-2.21-.894-4.208-2.343-5.657a1 1 0 010-1.414zm-2.829 2.828a1 1 0 011.415 0A5.983 5.983 0 0115 10a5.984 5.984 0 01-1.757 4.243 1 1 0 01-1.415-1.415A3.984 3.984 0 0013 10a3.983 3.983 0 00-1.172-2.828 1 1 0 010-1.415z" clip-rule="evenodd"></path>
        </svg>
        </button>
    </div>
    <div id="bar-wrap">
        <div id="bar" style="width: 0%;"></div>
    </div>
</div>

> "I drink 14 pints of mouthwash rations per week. At the rate... I think I'm
> going to poison myself to death... before I ever get to see the world again,
> which makes me feel... very sad. > I gotta change my program. I gotta go in a
> new direction. Anything I can do to keep my hands busy, I'm gonna do.
> Otherwise... I think maybe it's gonna be a suicide. And that's why I signed up
> for clay pottery and basket weaving. My name is Moses." ——《The French
> Dispatch》
