---
title: 在 Gatsby 中套用樣式
typora-copy-images-to: ./
disableTableOfContents: true
---

<!-- Idea: Create a glossary to refer to. A lot of these terms get jumbled -->

<!--
  - Global styles
  - Component css
  - CSS-in-JS
  - CSS Modules

-->

歡迎來到 Gatsby 教學的第二部分！

## 這篇教學裡有什麼？

在這個部分，你會探索為 Gatsby 網站套用樣式的一些方法，並且更深入地使用 React component 建立網站。

## 使用全域樣式

每個網站都有某些全域樣式，包含網站的文字排版與背景顏色。這些樣式決定了網站的整體氣氛──就好像牆壁的顏色與材質決定了一個房間的整體氣氛。

### 用標準的 CSS 檔案建立全域樣式

將全域樣式加入網站最直覺的方法之一就是使用全域的 `.css` 樣式表。

#### ✋ 建立新的 Gatsby 網站

先從建立新的 Gatsby 網站開始。最好關閉你在[第一部分](/tutorial/part-one/)中使用的終端機視窗，再為了第二部分重開一個終端機視窗。（尤其如果你對命令行介面不熟悉的話）

開啟新的終端機視窗，建立新的 "hello world" Gatsby 網站在 `tutorial-part-two` 的目錄內，然後進入這個新目錄：

```shell
gatsby new tutorial-part-two https://github.com/gatsbyjs/gatsby-starter-hello-world
cd tutorial-part-two
```

你現在有了新的 Gatsby 網站（以 Gatsby "hello world" starter 為基礎），它的結構如下：

```text
├── package.json
├── src
│   └── pages
│       └── index.js
```

#### ✋ 加入樣式至 css 檔案中

1. 在你的新專案中新增一個 `.css` 檔案：

```shell
cd src
mkdir styles
cd styles
touch global.css
```

> 注意：如果你比較偏好使用程式碼編輯器，也可以用你的程式碼編輯器新增這些資料夾跟檔案。

你現在應該會有像這樣的結構：

```text
├── package.json
├── src
│   └── pages
│       └── index.js
│   └── styles
│       └── global.css
```

2. 在 `global.css` 中定義一些樣式：

```css:title=src/styles/global.css
html {
  background-color: lavenderblush;
}
```

> 注意：範例的 css 檔案可以隨意的放在 `/src/styles/` 資料夾中的任何位置。

#### ✋ 在 `gatsby-browser.js` 引入樣式表

1. 新增 `gatsby-browser.js`

```shell
cd ../..
touch gatsby-browser.js
```

專案的檔案結構現在看起來會像這樣：

```text
├── package.json
├── src
│   └── pages
│       └── index.js
│   └── styles
│       └── global.css
├── gatsby-browser.js
```

> 💡 `gatsby-browser.js` 是什麼？先不要太擔心這個。現在只要知道 `gatsby-browser.js` 是 Gatsby 少數會尋找與使用的特殊檔案之一（如果它們存在）。在這裡，檔案的名字**很重要**。如果你現在想知道更多，請看[這份文件](/docs/browser-apis/)。

2. 引入剛剛新增的樣式表至 `gatsby-browser.js` 檔案：

```javascript:title=gatsby-browser.js
import "./src/styles/global.css"

// 或：
// require('./src/styles/global.css')
```

> 注意：CommonJS（`require`）跟 ES 模組（`import`）的語法在這邊都可以用。如果你不確定要選哪一個，`import` 通常是不錯的預設選項。然而如果是只在 Node.js 環境執行的檔案（像是 `gatsby-node.js`），則必須使用 `require`。

3. 啟動開發伺服器：

```shell
gatsby develop
```

如果你在瀏覽器中檢視你的專案，應該會看到 "hello world" starter 套用了淡紫色的背景：

![Lavender Hello World!](global-css.png)

> 提示：這一部分的教學集中於以最快速、直覺的方法為 Gatsby 網站套用樣式──直接使用 `gatsby-browser.js` 引入標準的 CSS 檔案。在大多數情況中，加入全域樣式的最佳方法是用共享的 layout component。[參閱這份文件](/docs/global-css/)以取得關於這個方法的更多資訊。

## 使用 component-scoped CSS

目前為止，我們談了比較傳統的方法，也就是使用標準的 CSS 樣式表。現在我們將說明各種模組化 CSS 的方法，讓我們能以 component 導向的方式處理樣式。

### CSS Module

讓我們研究 **CSS Module** 吧。引用自
[CSS Module 官網](https://github.com/css-modules/css-modules)：

> **CSS Module** 是一個 CSS 檔案，裡面所有類別與動畫的名字的作用範圍
> 預設都只在模組內。

CSS Module 非常受歡迎，因為它讓你能夠像平常一樣的寫 CSS，卻又更安全。這個工具自動生成唯一的類別與動畫的名字，所以你不需要擔心選擇器名稱會重複。

Gatsby 可以直接使用 CSS Module。這個方法非常推薦初次用 Gatsby（以及 React）開發的人使用。

#### ✋ 用 CSS Module 建立新頁面

在這一節，你會建立新的頁面 component，並且用 CSS Module 在頁面套用樣式。

首先，建立新的 `Container` component。

1. 在 `src/components` 新增一個新的資料夾，然後在這個新資料夾，新增一個叫做 `container.js` 的檔案，並貼上下列內容：

```jsx:title=src/components/container.js
import React from "react"
import containerStyles from "./container.module.css"

export default ({ children }) => (
  <div className={containerStyles.container}>{children}</div>
)
```

你會注意到你引入了一個 css module 檔案叫做 `container.module.css`。現在讓我們來新增那個檔案。

2. 在同一個資料夾裡（`src/components`）新增 `container.module.css` 檔案，並且複製貼上下面的內容：

```css:title=src/components/container.module.css
.container {
  margin: 3rem auto;
  max-width: 600px;
}
```

你會發現檔名以 `.module.css` 結尾，而不是平常的 `.css`。這告訴 Gatsby 這個 CSS 檔案應該當作 CSS module 處理，而不是純 CSS。

3. 新增 `src/pages/about-css-modules.js` 檔案以建立新的頁面 component：

```jsx:title=src/pages/about-css-modules.js
import React from "react"

import Container from "../components/container"

export default () => (
  <Container>
    <h1>About CSS Modules</h1>
    <p>CSS Modules are cool</p>
  </Container>
)
```

現在如果你瀏覽 `http://localhost:8000/about-css-modules/`，你的頁面看起來會像這樣：

![有 CSS module 樣式的頁面](css-modules-basic.png)

#### ✋ 使用 CSS Module 為 component 套用樣式

在這一節，你會建立一個列表，裡面有人名、大頭貼以及一段簡短的拉丁文介紹。你會建立 `<User />` component 並使用 CSS module 為那個 component 套用樣式。

1. 新增 `src/pages/about-css-modules.module.css` 檔案。

2. 在新的檔案裡貼上下列內容：

```css:title=src/pages/about-css-modules.module.css
.user {
  display: flex;
  align-items: center;
  margin: 0 auto 12px auto;
}

.user:last-child {
  margin-bottom: 0;
}

.avatar {
  flex: 0 0 96px;
  width: 96px;
  height: 96px;
  margin: 0;
}

.description {
  flex: 1;
  margin-left: 18px;
  padding: 12px;
}

.username {
  margin: 0 0 12px 0;
  padding: 0;
}

.excerpt {
  margin: 0;
}
```

3. 編輯前面幾行，以引入新的 `src/pages/about-css-modules.module.css` 檔案至先前建立的 `about-css-modules.js` 頁面，像這樣：

```javascript:title=src/pages/about-css-modules.js
import React from "react"
// highlight-next-line
import styles from "./about-css-modules.module.css"
import Container from "../components/container"

// highlight-next-line
console.log(styles)
```

`console.log(styles)` 這行程式碼會記錄引用的結果，所以你可以看到已處理過的 `./about-css-modules.module.css` 檔案。如果開啟你瀏覽器中的主控台（使用像是 Firefox 或 Chrome 的開發人員工具，通常是使用 F12 按鍵），你會看到：

![主控台中的 CSS module 引入結果](css-modules-console.png)

如果將那個跟你的 CSS 檔案比較，你會看到每一個類別現在都是已引入物件中的一個鍵，指向一個長字串，比如說 `avatar` 指向 `src-pages----about-css-modules-module---avatar---2lRF7`。這些是 CSS Module 產生的類別名字。這些名字在你的網站內都保證是唯一的。而且因為你必須引入它們來使用類別，你對某一段 CSS 程式碼在哪裡使用有疑問。

4. 在 `about-css-modules.js` 頁面 component 裡面建立新的 `<User />` component。修改 `about-css-modules.js` 讓它看起來像：

```jsx:title=src/pages/about-css-modules.js
import React from "react"
import styles from "./about-css-modules.module.css"
import Container from "../components/container"

console.log(styles)

// highlight-start
const User = props => (
  <div className={styles.user}>
    <img src={props.avatar} className={styles.avatar} alt="" />
    <div className={styles.description}>
      <h2 className={styles.username}>{props.username}</h2>
      <p className={styles.excerpt}>{props.excerpt}</p>
    </div>
  </div>
)
// highlight-end

export default () => (
  <Container>
    <h1>About CSS Modules</h1>
    <p>CSS Modules are cool</p>
    {/* highlight-start */}
    <User
      username="Jane Doe"
      avatar="https://s3.amazonaws.com/uifaces/faces/twitter/adellecharles/128.jpg"
      excerpt="I'm Jane Doe. Lorem ipsum dolor sit amet, consectetur adipisicing elit."
    />
    <User
      username="Bob Smith"
      avatar="https://s3.amazonaws.com/uifaces/faces/twitter/vladarbatov/128.jpg"
      excerpt="I'm Bob Smith, a vertically aligned type of guy. Lorem ipsum dolor sit amet, consectetur adipisicing elit."
    />
    {/* highlight-end */}
  </Container>
)
```

> 提示：一般而言，如果你在一個網站的多個地方使用一個 component，它應該在 `components` 資料夾有自己的模組檔案。但是如果只在一個地方用到，就在行內建立。

完成的頁面現在應該像：

![使用 CSS module 的使用者列表頁面](css-modules-userlist.png)

### CSS-in-JS

CSS-in-JS 是以 component 為導向的一種套用樣式的方法。最常見的情況中，它是一種模式，[使用 JavaScript 將 CSS 編排於行內](https://reactjs.org/docs/faq-styling.html#what-is-css-in-js)。

#### 在 Gatsby 使用 CSS-in-JS

有很多不同的 CSS-in-JS 程式庫，其中很多都已經有 Gatsby 插件。我們在這個一開始的教學中不會涵蓋 CSS-in-JS 的範例，但是我們鼓勵你[探索](/docs/styling/)這個生態系可以提供的東西。有兩個程式庫的迷你教學，特別是 [Emotion](/docs/emotion/) 與 [Styled Components](/docs/styled-components/)。

#### CSS-in-JS 的建議閱讀

如果你有興趣進一步閱讀關於這方面的資料，請參閱 [Christopher "vjeux" Chedeau 在 2014 年引發這場運動的簡報](https://speakerdeck.com/vjeux/react-css-in-js)以及 [Mark Dalgleish 比較新的文章「統一的樣式語言」](https://medium.com/seek-blog/a-unified-styling-language-d0c208de2660)。

### 其他 CSS 選擇

Gatsby 支援幾乎每一種可能的樣式套用選項（如果你最喜歡的選擇還沒有插件，[請幫它貢獻一個！](/contributing/how-to-contribute/)）

- [Typography.js](/packages/gatsby-plugin-typography/)
- [Sass](/packages/gatsby-plugin-sass/)
- [JSS](/packages/gatsby-plugin-jss/)
- [Stylus](/packages/gatsby-plugin-stylus/)
- [PostCSS](/packages/gatsby-plugin-postcss/)

還有更多！

## 接下來是什麼？

現在繼續進行[教學的第三部分](/tutorial/part-three/)，在那裡你將學到 Gatsby 插件與 layout component。
