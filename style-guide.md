# 風格指南

使用此文件以遵循特定語言的樣式規則進行翻譯。

## 規則

### 在代碼區塊中的文字

在代碼區塊中的文字不應該予以翻譯，註解除外。翻譯字串是非強制的，但必須注意跟代碼之間的關係。

例子:

```js
// example
import React from "react"
export default () => (
  <div style={{ color: `purple`, fontSize: `72px` }}>Hello Gatsby!</div>
)
```

✅ 可以這樣做：

```js
// 例
import React from "react"
export default () => (
  <div style={{ color: `purple`, fontSize: `72px` }}>Hello Gatsby!</div>
)
```

✅ 也可以這樣做：

```js
// 例
import React from "react"
export default () => (
  <div style={{ color: `purple`, fontSize: `72px` }}>你好！蓋茲比</div>
)
```

❌ 不可以這樣做：

```js
// 例
import React from "react"
export default () => (
  // 'purple' is a CSS keyword
  <div style={{ color: `紫色`, fontSize: `72px` }}>你好！蓋茲比</div>
)
```

❌ 絕對避免：

```js
importar 反應 從 "反應"
輸出 默認值  () => (
   <div 風格 = {{color: `紫色`, fontSize:` 72px`}}>你好！蓋茲比</div>
)
```

### 外部連結

如果有一個外部連結連到一篇[MDN] 或 [Wikipedia] 的文章，而該文章已經有相當不錯的繁體中文版，最好連結到該頁面。

[mdn]: https://developer.mozilla.org/zh-TW/
[wikipedia]: https://zh.wikipedia.org/zh-tw/

例

```md
React elements are [immutable](https://en.wikipedia.org/wiki/Immutable_object).
```

✅ OK:

```md
React元件為[不可變元件](https://zh.wikipedia.org/wiki/%E4%B8%8D%E5%8F%AF%E8%AE%8A%E7%89%A9%E4%BB%B6).
```

如果該連結並沒有中文版 (Stack Overflow, YouTube影片等等)，請直接使用英文版連結。

## 通用詞彙

使用這個區塊來列出常見詞彙的正確翻譯

| 術語    | 翻譯 |
| ------ | ----------- |
| Plugin | 插件         |
| Theme  | 主題         |
| Query  | 查詢         |
