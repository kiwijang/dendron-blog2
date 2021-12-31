---
id: DTeYpEuPv3KIHugUyqZPu
title: 1226 First Day
desc: ""
updated: 1640962046607
created: 1640525260857
tags:
  - PROG.Dendron
---

## 首次使用 Dendron 紀錄

### 建置並預覽筆記

- Preview
  http://localhost:3000 在本機查看網站，`CTRL-C` 離開終端機。
  `npx dendron publish dev`

- Publish
  以 target github 輸出網站
  `npx dendron publish export --target github`

參考資料:
https://wiki.dendron.so/notes/yg3EL1x9fEe4NMqxUC3jP/

---

### .next 專案 fork 來源

https://github.com/dendronhq/nextjs-template

---

## 問題紀錄

### github page build 失敗

```bash
  /usr/bin/git submodule sync
  Error: fatal: No url found for submodule path '.next' in .gitmodules
```

![](/assets/images/2021-12-31-19-23-24.png)

解答: https://stackoverflow.com/questions/4185365/no-submodule-mapping-found-in-gitmodule-for-a-path-thats-not-a-submodule

- 問題起因: `git submodule update --init` 發生 No submodule mapping found in .gitmodules 問題。

覺得應該是一開始我 `git init` 時，忘記先將 .next 排除版控 `echo .next >> .gitignore`。

造成 .git 版控出了一些問題 (.next 自己也有一個 .git 版控)，執行下面的指令後就好了。

- `git rm --cached .next`

  [git 官網參數說明](https://git-scm.com/docs/git-rm)

  ```bash
  --cached
  Use this option to unstage and remove paths only from the index.
  Working tree files, whether modified or not, will be left alone.
  ```

  取消追蹤 .next 資料夾版控後，github page build 就可以順利完成 github page 的 build 了 😄

### npx dendron publish dev ctrl+c 以後 port 沒有清掉

`netstat -a` 查看使用中連線

`npx kill-port 3000` 清除 3000 port

參考網址: https://stackoverflow.com/questions/39632667/how-do-i-kill-the-process-currently-using-a-port-on-localhost-in-windows
