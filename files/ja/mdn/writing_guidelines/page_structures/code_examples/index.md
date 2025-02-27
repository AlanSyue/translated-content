---
title: コードサンプル
slug: MDN/Writing_guidelines/Page_structures/Code_examples
page-type: mdn-writing-guide
tags:
  - meta
  - writing-guide
translation_of: MDN/Writing_guidelines/Page_structures/Code_examples
original_slug: MDN/Writing_guidelines/Page_structures/Code_examples
---

{{MDNSidebar}}

MDN では、ウェブプラットフォームの機能の使い方を示すために、ページ中に数多くのコードサンプルが挿入されています。この記事では、ページにコードサンプルを追加するためのさまざまな仕組みと、どのような場合にどのような仕組みを使うべきかについて説明します。

> **Note:** もし、コードを入れる様々な方法ではなく、 MDN の記事に現れるコードのスタイルやゴミ取りについてアドバイスが欲しいなら、[コードスタイルガイド](/ja/docs/MDN/Writing_guidelines/Writing_style_guide/Code_style_guide)を参照してください。

## 利用できるコードサンプルの種類

MDN には 4 種類のコードサンプルがあります。

- 静的サンプル — プレーンなコードブロックで、そのようなコードを実行した場合の結果を静的に示すスクリーンショットが付いている場合があります。
- インタラクティブサンプル - [ライブでインタラクティブサンプル](https://github.com/mdn/interactive-examples)を生成するためのシステムで、コードをライブで表示するだけでなく、その場でコードを変更して効果を確認したり、結果を簡単にコピーしたりすることができます。
- MDN の従来型「ライブサンプル」 - 単体のコードブロックを {{htmlelement("iframe")}} 要素内の文書に動的に配置し、ページに埋め込んでコードの実行をライブで表示するマクロです。
- GitHub の「ライブサンプル」 —  [mdn 組織](https://github.com/mdn/)内の GitHub リポジトリーにある文書を取り込んで {{htmlelement("iframe")}} 要素の中に入れ、それをページに埋め込んでコードをライブで表示するマクロです。

それぞれの機能については後のセクションで説明します。

## 使うべき場面

コードサンプルの種類ごとに、それぞれの用途があります。どのような場合に使用するのでしょうか。

- 静的サンプルは、単にコードを表示するだけで、実際の結果を表示することがそれほど重要でない場合に便利です。何かをコピー＆ペーストだけしたいという人もいます。中間段階を示すだけの場合や、ソースコードで十分な場合もあるでしょう。(例えば、上級者向けの記事で、コードを見てもらえればよい場合など) また、埋め込み型のサンプルではうまくいかない API 機能のデモを行っている場合もあり、その場合はリンク先として別のページが必要になるかもしれません。
- インタラクティブサンプルは、読者がその場で値を変更できるので、学習には非常に有効です。しかし、他のフォームよりも設定が複雑で、制限も多く、特定の目的のためのものです。
- 従来型ライブサンプルは、ページ上にソースコードを表示し、それを実行する様子を見せたい場合で、独立したサンプルとしてアクセスできるかどうかはそれほど気にしない場合に便利です。この方法は、ソースコードとライブサンプルを並べて表示した場合、コードを一度更新するだけで両方を更新できるという利点があります。しかし、編集したり動作させたりするのが面倒なこともあります。
- GitHub ライブサンプルは、既存のサンプルを埋め込んでソースコードを見せたくないときや、そのサンプルがスタンドアロンで利用できることを確認したいときなどに便利です。協力するためのワークフローはより優れていますが、 GitHub を知っている必要があります。また、ページ上のコードとソースコードが 2 つの異なる場所にあるため、同期が取れなくなることもあります。

## 一般的なガイドライン

MDN でサンプルを追加・更新する際には、上記のようなライブサンプルを表示するための具体的なシステムの他に、スタイルやコンテンツについても考慮する必要があります。

- サンプルをページに掲載する際には、書かれている API や概念のすべての機能やオプションをカバーするようにしてください。最低でも、最も一般的なオプションやプロパティはサンプルに含めるべきです。
- それぞれのサンプルの前で、そのサンプルが何をしているのか、なぜそれが興味深いのか、役に立つのかを説明してください。
- コードのそれぞれの部分の後には、それが何をするものなのかを説明してください。
- 可能な限り、大きなサンプルは小さく分割してください。例えば、「ライブサンプル」システムでは、サンプルを実行する前に、すべてのコードを自動的に 1 つにまとめてくれますが、実際には、JavaScript、HTML、CSS をより細かく分割し、それぞれの部分の後に説明文を付けることができます。これは、長いコードや複雑なコードをよりわかりやすく説明するためのよい方法です。
- API や技術の各部分がどのように機能するかを説明するだけではありません。実際の使用例を考慮した上で、実演してみましょう。

## 静的サンプル

静的サンプルでは、ある機能がコードでどのように使用されるかを示す静的なコードブロックについて話しています。これらは[コード例ブロック](/ja/docs/MDN/Writing_guidelines/Howto/Markdown_in_MDN#コードブロックの例)で記述されているように、 Markdown の「コードフェンス」を使ってページに配置されます。結果の例は次のようになります。

```js
// これは JS の例です
const test = "Hello";
console.log(test);
```

任意で、次のように出力結果を静的な画像で示すことができます。

![Screenshot of a console output in developer tools](console-example.png)

## インタラクティブサンプル

インタラクティブなサンプルは、 MDN のリファレンスページの上部で使用されることを想定しています。初心者や、調べていることの詳細を見る前に、すぐに例題を手に取って遊びたいという読者にとっての価値を高めるために、これらを提供することを目指しています。インタラクティブサンプルについては、いくつかの重要な制限事項があります。

- インタラクティブサンプルは、特定の技術に特化しています。 — JavaScript の UI と CSS の UI は異なりますし、 1 つの技術を独立させて説明しているだけです。例えば、特定の HTML/CSS/JS 構造をどのように組み合わせるかを示したい場合には適していません。
- インタラクティブなライブサンプルは、現在のところ CSS と JavaScript を表示するように設定されています。他の技術については、待つしかありません。
- UIは他のコード例よりもパフォーマンスを重視していますので、適用する MDN の記事ごとに複数を置くべきではありません。
- 長いコードサンプルには適していません。 — この UI は本当に短い (10-15 行程度) サンプルでのみ利用できる固定された大きさの範囲でのみ有効です。

サンプルを投稿したい場合は、 [interactive examples repo Contribution guide](https://github.com/mdn/interactive-examples/blob/main/CONTRIBUTING.md) でその方法を知ることができます。

関連するインタラクティブサンプルがないページを見つけた場合は、ぜひ投稿してください。

### インタラクティブサンプルのデモ

[`EmbedInteractiveExample`](https://github.com/mdn/yari/blob/main/kumascript/macros/EmbedInteractiveExample.ejs) マクロを使用して、完成したサンプルを MDN ページに埋め込みます。たとえば、 \\{{EmbedInteractiveExample("pages/js/array-push.html")}} というマクロ呼び出しで、次のコードサンプルが表示されます。

{{EmbedInteractiveExample("pages/js/array-push.html")}}コードを調整して様子を見たり、操作をしたりしてみてください。

## 従来型ライブサンプル

従来型ライブサンプルは、 [`EmbedLiveSample`](https://github.com/mdn/yari/blob/main/kumascript/macros/EmbedLiveSample.ejs) マクロを使ってページに挿入します。 \\{{EmbedLiveSample}} を呼び出すと、自分と同じ文書の節にあるコードブロックを動的に取得して文書に入れ、それを {{htmlelement("iframe")}} の中のページに挿入します。詳しくは[ライブサンプルガイド](/ja/docs/MDN/Writing_guidelines/Page_structures/Live_samples)をご覧ください。

### ライブサンプルの書式設定

この「例」セクションにライブサンプルを書く場合は、このライブサンプルの例を説明する H3 見出し (`###`) を提供してください。理想的には、シナリオと何を実証することを期待しているのかを説明して、その例の短い説明を書いてください。次に、以下の H4 見出し (`####`) を付けたサブセクションを、リスト順に追加してください。

- HTML
- CSS
- JavaScript
- Result
上記のそれぞれのサブセクションにコードブロックを書きます。
**結果**サブセクションに、 [`EmbedLiveSample` マクロ](/ja/docs/MDN/Writing_guidelines/Page_structures/Live_samples#live_sample_macros)への呼び出しを追加してください。できれば、このサブセクションに、結果を記述するための文章をもう少し入れてください。
もし、特定の言語型を使用しない場合（例えば、 JavaScript を使用しない場合）、または非表示にしている場合は、対応する見出しを省略する必要があります。

例

````
## 例

### 段落のスタイル設定

この例では、 `fancy` クラスが設定されている段落にスタイルを設定するために CSS を使用しています。

#### HTML

```html
<p>I'm not fancy.</p>

<p class="fancy">But I am!</p>
```

#### CSS

```css
p.fancy {
  color: red;
}
```

#### 結果

\{{EmbedLiveSample("Styling a paragraph")}}

`<p>` 要素のうち `class="fancy"` の付いたものだけが、 `red` のスタイルになります。
````

### 非表示のコード

ページ内に表示される例に関連する静的なコードブロックを表示したいだけの場合があります。しかし、そのような例を表示するためには、HTML、CSS、JavaScript が必要です。

これを実現するために、 `hidden` クラスを使って、関連性のないコードブロックを隠すことができます。

上記の例を使用し、 HTML コードを非表示にすると、次のようになります。

````
## 例

### 段落のスタイル設定

この例では、 `fancy` クラスが設定されている段落にスタイルを設定するために CSS を使用しています。

#### HTML

```html hidden
<p>I'm not fancy.</p>

<p class="fancy">But I am!</p>
```

#### CSS

```css
p.fancy {
  color: red;
}
```

#### 結果

\{{EmbedLiveSample("Styling a paragraph")}}

`<p>` 要素のうち `class="fancy"` の付いたものだけが、 `red` のスタイルになります。
````

## GitHub ライブサンプル

GitHub ライブサンプルは、 [`EmbedGHLiveSample`](https://github.com/mdn/yari/blob/main/kumascript/macros/EmbedGHLiveSample.ejs) マクロを使ってページに挿入します。\{{EmbedGHLiveSample}} を呼び出すと、指定した URL (GitHub の mdn 組織内のものでなければなりません) の文書を動的に取得し、ページ内の {{htmlelement("iframe")}} 内に挿入します。

これらは従来のライブサンプルとよく似た動作をしますが、よりシンプルなものです。

ページ上のコードブロックの配置を気にする必要はありません。 GitHub リポジトリーの HTML 文書を取得して、`<iframe>` の中に挿入します。

マクロの引数は 3 つだけです。

1. 埋め込む文書の URL — これは、 `https://mdn.github.io/` にある最上位のディレクトリである mdn 組織からの相対 URL です。ですから、この引数には、`my-subdirectory/example.html` のように、URL の後の部分を含める必要があります。 `index.html` の場合は、ファイル名を省略できます。
2. `<iframe>` の幅、パーセント値またはピクセル単位で表すことができます。
3. `<iframe>` の高さ、パーセント値またはピクセル単位で表すことができます。

例を見てみましょう。 [https://mdn.github.io/learning-area/css/styling-boxes/backgrounds/](https://mdn.github.io/learning-area/css/styling-boxes/backgrounds/) のコードを埋め込みたいとします。次のように呼び出すことができます。

\\{{EmbedGHLiveSample("learning-area/css/styling-boxes/backgrounds/", '100%', 100)}}

表示されるときには次のようになります。

{{EmbedGHLiveSample("learning-area/css/styling-boxes/backgrounds/", '100%', 100)}}

### GitHub ライブサンプルを使用するためのヒント

- まず最初に、適切なコードサンプルを [GitHub の mdn 組織](https://github.com/mdn/)に登録する必要があります。これは Git を使って行う必要があります。 Git に慣れていない方は、 [GitHub ページの使い方](/ja/docs/Learn/Common_questions/Using_Github_pages)の記事を参照してください。もっと慣れている人は[データを追加する準備](/ja/docs/MDN/Writing_guidelines/Page_structures/Compatibility_tables#preparing_to_add_the_data)を参照してください。
- コードサンプルは、実証しようとしていることを示すのに適したものでなければなりません。 1 つのことをうまく行う簡単なサンプルが含まれていること、不快な内容が含まれていないこと、そして MDN の[コードサンプルガイドライン](/ja/docs/MDN/Writing_guidelines/Writing_style_guide/Code_style_guide)に従っている必要があります。
