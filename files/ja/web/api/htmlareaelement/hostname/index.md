---
title: HTMLAreaElement.hostname
slug: Web/API/HTMLAreaElement/hostname
page-type: web-api-instance-property
tags:
  - API
  - HTMLAreaElement
  - プロパティ
  - リファレンス
browser-compat: api.HTMLAreaElement.hostname
translation_of: Web/API/HTMLAreaElement/hostname
original_slug: Web/API/HTMLHyperlinkElementUtils/hostname
---
{{ApiRef("HTML DOM")}}

**`HTMLAreaElement.hostname`** プロパティは、URL のドメインを含む文字列です。

## 値

`area` 要素に関連付けられた URL のドメインを含む文字列です。
セッターとゲッターの両方として使用することができます。

## 例

```html
<textarea id="log" rows="4" cols="100"></textarea>
<map name="infographic">
    <area id="area1" shape="rect" coords="184,6,253,27"
          href="/en-US/docs/HTMLAreaElement"
          target="_blank" alt="Mozilla" />
    <area id="area2" shape="circle" coords="130,136,60"
          href="https://coolexample.com/"
          target="_blank" alt="MDN" />
</map>
```

```js
// 要素が文書内にあったとします
const area1 = document.getElementById("area1");
const area2 = document.getElementById("area2");

const log = document.getElementById("log");
log.textContent = `area1 hostname: ${ area1.hostname } \n`; // 'developer.mozilla.org'
log.textContent += `area2 hostname: ${ area2.hostname }`;  // 'coolexample.com'
```

{{EmbedLiveSample("Examples")}}

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- 所属先の {{domxref("HTMLAreaElement")}} インターフェイス
