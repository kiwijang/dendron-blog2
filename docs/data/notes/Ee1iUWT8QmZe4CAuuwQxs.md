
## 前言

> 深入淺出 Monorepo 架構 — 使用 Nx Console 實現一個 Monorepo 架構的專案

導讀影片: [Monorepos - How the Pros Scale Huge Software Projects // Turborepo vs Nx](https://www.youtube.com/watch?v=9iU_IE6vnJ8)

## 簡介 Monorepo 架構

Monorepo (全名 Monolithic Repository)，符合以下三個條件:

1. One Repository
2. Multiple projects
3. Shared Libraries

如下圖，可以看到:

1. **一個 repo**
2. **多個 projects** (三個 app 加上兩個 libs)
3. **共用 libs**。

![MonoRepo](assets/images/2021-12-27-22-50-05.png)

Monorepo 架構的主要目的是希望集中管理套件版本。

透過只管理一個 `package.json`，可以發現好處是套件版本管理方便、而壞處是一個 repo 有多個 projects，檔案容易變非常大，讓 git 版控軟體跑起來較吃力。

另外 Monorepo 讓 apps 之間共用 libs 變得方便簡單，所以可以降低重複程式碼的機率。
也可以讓 Lerna、yarn 等套件管理工具更方便的減少重複的套件安裝。

而以 Nx 來說，更酷的特色是可以在同一個 repo 裡同時使用 react 和 angular 共同開發一個 app。

雖然也可以使用 rollupjs 來達到不同前端框架共同開發一個 app 的效果。

但 Nx 就像 monorepo 全家桶: 提供一個 Nx workspace 讓你的 monorepo 開發更容易。

接下來，在看看 Nx 之前，先來一些先備知識 😆

## 簡介 Nx 工具與專有名詞解釋

### 什麼是 Nx ?

官網: https://nx.dev/

![](assets/images/2021-12-27-23-55-50.png)

> Smart, Extensible Build Framework
> Nx helps architect, test, build at any scale:

- integrations with modern frameworks
- computation caching
- smart rebuilds of affected projects
- distributed task execution
- powerful code generators
- editor support (VSCode, WebStorm)
- GitHub apps
- and more.

### Nx 的製作團隊

narwhal 簡寫 Nrwl，是獨角鯨的英文。

![](assets/images/2021-12-27-23-57-12.png)

Consulting. Engineering. Training.
Nrwl was founded in December 2016 by Angular team members and former Googlers, Jeff Cross and Victor Savkin, and today has around 18 team members in the US, Canada and UK.
Nrwl is also the creator of open-source dev tools: Nx for monorepo development, and Angular Console.

### Angular monorepo patterns

這本書說明了 nx 是如何實踐 monerepo 概念

![](assets/images/2021-12-27-23-59-52.png)

- https://connect.nrwl.io/app/books
- https://nrwl.io/products

### Nx 與 Angular 淵源不淺

![](assets/images/2021-12-28-00-06-48.png)

上面這兩位 Nx 開發的主導者是 Google 的前員工，且對 Angular 都有相當深入的理解。
但 Nx 官網上有不少 react 的開發教學，如果有公司想要從 react 轉到 angular(或是 angular 轉 react 為主)，感覺透過 Nx 的幫助可以慢慢地移花接木(不然 Nx 也至少可以讓這兩框架和平共處 😆)

### Angular 詞彙表

- [Workspace](https://angular.tw/guide/glossary#workspace) (工作區)

  一個 Angular 所有專案的集合(可以用 Angular CLI 操作這個集合)，通常會在 git 版本控制的 repository 中。

- [Project](https://angular.tw/guide/glossary#project) (專案)

  可以通過 Angular CLI 命令創建或修改的獨立應用程式或函式庫。可在 angular.json 中配置 workspace 中的所有 projects。

- [Library](https://angular.tw/guide/glossary#library) (函式庫)

  一種 Angular 專案。用來讓其它 Angular 應用包含它，以提供各種功能。函式庫不是一個完整的 Angular 應用，不能獨立執行。

- [TypeScript 配置](https://angular.tw/guide/typescript-configuration#configuration-files)

  一個 Angular 工作區中包含多個 TypeScript 配置檔案。在 root，有兩個主要的 TypeScript 配置檔案：tsconfig.json 檔案和 tsconfig.app.json 檔案。[使用 extends 進行配置繼承](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html#tsconfig-bases)。

- [Schematic](https://angular.tw/guide/glossary#schematic) (原理圖)

  Angular CLI 使用原理圖來產生和修改 Angular 專案及其部件。

- Collection (集合)

  在 Angular 中，是指收錄在同一個 [npm 套件](https://angular.tw/guide/glossary#npm-package) 中的一組原理圖（schematics）。

  ![](assets/images/2021-12-28-00-23-52.png)

## 感受一下 Nx 的 monorepo 專案

- Angular workspace 的 libs 通常都會有一個自己的 `package.json`
  ![](assets/images/2021-12-28-00-29-52.png)

- Nx workspace 預設共用一個 `package.json`
  ![](assets/images/2021-12-28-00-28-00.png)

## 產生一個 Nx 的 workspace

## 快速上手 Nx Console 操作 (Generate、Run)

## 其他補充
