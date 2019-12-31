---
title: 快速入門
---

此快速入門指南是給中級到高級的工程師，更溫和的Gatsby入門請看[入門教學](/tutorial/)!

## 使用Gatsby CLI

<EggheadEmbed
  lessonLink="https://egghead.io/lessons/gatsby-quick-start-with-gatsby-create-develop-and-build-gatsby-sites-from-the-command-line"
  lessonTitle="Quick Start with Gatsby: Create, Develop, and Build Gatsby Sites From the Command Line"
/>

**注意**: 此影片使用`npx`，是一個免安裝直接啟動npm package的工具。運行指令`npx gatsby new`和安裝gatsby-cli在本機後並執行`gatsby new`是一樣的。

### 安裝Gatsby CLI

```shell
npm install -g gatsby-cli
```

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

Gatsby會啟動一個即時重載的開發環境，預設位址於`localhost:8000`。

試著在`src/pages`中編輯JavaScript頁面。保存的更動將即時重載到瀏覽器中。

### 建立一個生產環境(production build)

```shell
gatsby build
```

Gatsby會為你的網站創立一個優化過的生產環境(production build)，產生靜態HTML和不同路徑的JavaScript代碼封包。

### 生產環境放上本機伺服器

```shell
gatsby serve
```

Gatsby啟動一個本機HTML伺服器來測試你的網站。在使用此指令之前記得使用`gatsby build`。

### 查看CLI指令的文件

查看CLI指令的詳細文件，在終端機執行`gatsby --help`

特定的指令，執行`gatsby COMMAND_NAME --help` 例如 `gatsby new --help`.

更多關於Gatsby CLI的資訊，請查看 [CLI reference](/docs/gatsby-cli/)區塊。
