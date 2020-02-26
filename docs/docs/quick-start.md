---
title: 快速入門
---

此快速入門指南是給中級到高級的工程師，更溫和的 Gatsby 入門請看[入門教學](/tutorial/)!

## 使用 Gatsby CLI

<EggheadEmbed
  lessonLink="https://egghead.io/lessons/gatsby-quick-start-with-gatsby-create-develop-and-build-gatsby-sites-from-the-command-line"
  lessonTitle="快速開始使用 Gatsby: 在命令列內建立、開發和建構 Gatsby 網站"
/>

**注意**: 此影片使用 `npx`，是一個免安裝直接啟動 npm package 的工具。運行指令 `npx gatsby new` 和安裝 gatsby-cli 在本機後並執行 `gatsby new` 是一樣的。

### 安裝 Gatsby CLI

```shell
npm install -g gatsby-cli
```
使用上面指令將 Gatsby CLI 全域安裝於你的系統


### 建立一個新網站

```shell
gatsby new gatsby-site
```

### 變更目錄到網站資料夾

```shell
cd gatsby-site
```

### 啟動開發伺服器

```shell
gatsby develop
```

Gatsby 會啟動一個即時重載的開發環境，預設位址於 `localhost:8000`。

試著在 `src/pages` 中編輯 JavaScript 頁面。保存的更動將即時重載到瀏覽器中。

### 建立一個生產環境 (production build)

```shell
gatsby build
```

Gatsby 會為你的網站創立一個優化過的生產環境 (production build)，產生靜態 HTML 和不同路徑的 JavaScript 代碼封包。

### 生產環境放上本機伺服器

```shell
gatsby serve
```

Gatsby 啟動一個本機 HTML 伺服器來測試你的網站。在使用此指令之前記得使用 `gatsby build`。

### 查看 CLI 指令的文件

查看 CLI 指令的詳細文件，在終端機執行 `gatsby --help`

特定的指令，執行 `gatsby COMMAND_NAME --help` 例如 `gatsby new --help`.

更多關於 Gatsby CLI 的資訊，請查看 [CLI reference](/docs/gatsby-cli/)區塊。
