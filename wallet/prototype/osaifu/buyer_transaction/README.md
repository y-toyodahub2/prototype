# App Prototype

## セットアップ

```bash
git clone https://github.com/kouzoh/zp-mhigashino.git
cd zp-mhigashino/prototype/transaction
```

## ブラウザ閲覧

```
https://miniature-lamp-1qq4n9l.pages.github.io/transaction/
```

- GitHub Pages で公開しています（`main` ブランチへの push で自動デプロイ）
- リポジトリは private のため、閲覧にはリポジトリへのアクセス権限が必要です

### Safari PWA（推奨）

iPhoneのSafariで開き、「ホーム画面に追加」するとPWAとして起動できます。OSのアドレスバーやタブバーが非表示になり、よりネイティブアプリに近い見た目で確認できます

1. SafariでGitHub PagesのURLを開く
2. 共有ボタン → 「ホーム画面に追加」
3. ホーム画面のアイコンから起動


## Claude Code 設定

このプロトタイプは [Claude Code](https://claude.com/claude-code) で開発・管理されています。

- `CLAUDE.md` — プロトタイプの編集ルール・実装済み挙動仕様・画面構成などを定義しています。Claude Code はこのファイルを参照してコード生成・編集を行います
- DSスキル `ds-prototype` — Mercari DS4 のデザイントークン・コンポーネントルールをまとめたスキル。**リポジトリルートの `zp-kazuya/.claude/skills/ds-prototype/SKILL.md` に集約**されており、各プロトタイプ配下から git root 経由で自動参照されます（個別配置は不要）

## ファイル構成

```
index.html               # メインファイル（全画面・CSS・JSを含む）
assets/
  items/                 # 商品画像（Google Driveから取得した実商品画像）
  images/                # その他画像（UI素材・背景等）
  icons/
    fill/                # Fill スタイルSVGアイコン（119個）
    outline/             # Outline スタイルSVGアイコン（185個）
CLAUDE.md                # Claude Code向け開発ルール
```

> DSスキル本体（`ds-prototype/SKILL.md`）はリポジトリルートの `.claude/skills/` に集約。本プロトタイプ固有の差分が必要になった場合のみ、本ディレクトリ配下に `.claude/skills/ds-prototype/SKILL.md` を作成して override します。

### アイコンについて

`assets/icons/` には [kouzoh/merui-web](https://github.com/kouzoh/merui-web) の `@kouzoh/merui-icons` パッケージからコピーしたSVGアイコンが格納されています。

- `assets/icons/fill/` — Fill スタイル（119個）
- `assets/icons/outline/` — Outline スタイル（185個）

使用する際はSVGファイルをインラインで展開し、`color` CSSプロパティで色を制御してください。

## Lottieアニメーション

アニメーションには [lottie-web](https://github.com/airbnb/lottie-web) を使用しています。

- CDN経由で読み込み（`<head>` 内の `<script src="https://cdnjs.cloudflare.com/ajax/libs/lottie-web/5.12.2/lottie.min.js">`）
- JSONファイルは `assets/images/` に配置
- `lottie.loadAnimation()` で初期化し、2回目以降は `goToAndPlay(0, true)` で再生

現在使用中のアニメーション：
- `assets/images/mike-THX.json` — 購入完了ダイアログ（`#purchase-lottie`）

## 注意事項

### 商品画像について

商品画像は `assets/items/` フォルダのものを使用しています。

画像はプレスリリースなど、使用許諾のある商品画像を使用しており、[Google Drive](https://drive.google.com/drive/folders/1m04yIziHoVsNBr1ELR3zh2EDIA8TaihV?usp=drive_link) で管理されています。画像選定基準は [How to Choose Item Images (Notion)](https://www.notion.so/How-to-Choose-Item-Images-2767fa9ffaef80efaf3beb3efa8cca31) を参照してください。

### このプロトタイプについて

- あくまでデザイン検討用のプロトタイプとして擬似的に構築されたサイトです
- メルカリアプリ・メルカリWebのソースコードは使用していません
- UIのインタラクション（画面遷移・アニメーション等）はすべて Claude Code で生成したものです
