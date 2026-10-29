# 開発ガイド

Duel Five は、`index.html` を入口とする静的なブラウザゲームです。遊び方とライセンスはルートの [README](../README.md) を参照してください。

## 起動とビルド

Node.js 20 以上を使用します。追加パッケージのインストールは不要です。

```sh
npm run dev
npm test
npm run build
npm run preview
```

`npm run dev` はソースを、`npm run preview` はビルド後の `dist/` を配信します。既定ポートは 4173 です。サーバーは全ネットワークインターフェースで待ち受けるため、開発時は利用するネットワークに注意してください。`npm run build` は既存の `dist/` を削除して静的ファイルを再生成するので、生成物を直接編集しないでください。

## 主な構成

- `index.html`：画面の要素とアプリの読込入口。
- `src/game.js`：カード対決、CPU の選択、対戦と進行状態のルール。
- `src/app.js`：画面操作、描画、音、ブラウザ保存、結果共有。
- `src/style.css`：配色と画面レイアウト。
- `tests/game.test.mjs`、`tests/campaign.test.mjs`、`tests/social.test.mjs`：ルール、進行、共有用メタデータの検証。
- `scripts/serve.mjs`、`scripts/build.mjs`：開発用配信と静的ファイルの生成。

## 変更時の確認

ルールや保存形式を変えるときは `npm test` を実行し、対戦の進行と再読み込み後の復元を確認してください。画面や音を変えるときは、キーボード操作、配色切替、音の初期 OFF、動きを減らす設定、結果共有をブラウザでも確認してください。

配信版の識別子は `index.html`、`src/app.js`、`src/style.css` にまたがるため、更新時は整合させてください。素材を変更した場合は `README.md` の第三者素材表示と `LICENSE` も確認してください。
