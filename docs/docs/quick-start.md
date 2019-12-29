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

### 改變目錄進到網站資料夾

```shell
cd gatsby-site
```

### 啟動開發伺服器

```shell
gatsby develop
```

Gatsby will start a hot-reloading development environment accessible by default at `localhost:8000`.

Try editing the JavaScript pages in `src/pages`. Saved changes will live reload in the browser.

### Create a production build

```shell
gatsby build
```

Gatsby will perform an optimized production build for your site, generating static HTML and per-route JavaScript code bundles.

### Serve the production build locally

```shell
gatsby serve
```

Gatsby starts a local HTML server for testing your built site. Remember to build your site using `gatsby build` before using this command.

### Access documentation for CLI commands

To see detailed documentation for the CLI commands, run `gatsby --help` in the terminal.

For specific commands, run `gatsby COMMAND_NAME --help` e.g. `gatsby new --help`.

For more information on the Gatsby CLI, visit the [CLI reference](/docs/gatsby-cli/) section of the docs.
