# 研究者のための Quarto ガイド

Quarto・GitHub・Cloudflare を組み合わせて、研究にまつわる文章とコードを
「書く・管理する・公開する」ための教材です。大学院生と研究者を対象とし、
Git や Quarto にはじめて触れる人でも読み進められるように書いています。

公開先: https://maple60.github.io/quarto-for-research/

このリポジトリ自体が Quarto で書かれ、GitHub Actions で自動公開されています。
教材で説明している構成の、動く実例として参照できます。

> 現在は骨組みを作っている段階です。本文はこれから執筆します。

## ローカルでビルドする

[Quarto](https://quarto.org/docs/get-started/) をインストールしてから、
リポジトリのルートで次を実行します。

```bash
quarto preview
```

ブラウザが開き、`.qmd` ファイルを保存するたびに表示が更新されます。

ファイルを書き出すだけなら次を実行します。出力は `_site/` に入ります。

```bash
quarto render
```

スライドは `slides/` に置いた独立した Quarto プロジェクトです。
教材本体より **後に** ビルドしてください（先にビルドすると、
教材本体のレンダリングで出力が消えます）。

```bash
quarto render && quarto render slides
```

## 構成

| 場所 | 内容 |
|---|---|
| `index.qmd` | まえがき |
| `chapters/` | 各章の本文 |
| `slides/` | 発表スライド（Reveal.js） |
| `assets/` | テーマ・画像などの共有ファイル |
| `_quarto.yml` | 教材本体の設定 |
| `.github/workflows/publish.yml` | 自動ビルドと公開の設定 |

`_site/` と `.quarto/` はビルドで生成されるため、Git では追跡していません。

## 公開の仕組み

`main` ブランチに push すると GitHub Actions が動き、教材とスライドを
ビルドして GitHub Pages へ公開します。手元で `_site/` をコミットする
必要はありません。
