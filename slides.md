class: middle, center

<img src="./assets/logo.svg" align="center" width="200" />

Deno の最近の動向 2022

---
class: middle, center
資金調達 - 6月

$21M 調達

---
class: middle, center

Bun の登場 - 7月

---
class: middle, center

NPM 互換性リリース - 8月

---
class: middle, center

Deno Offsite - 10月

---
class: middle, center

イベントが盛りだくさんだった 2022

---
class: middle, center

2022 の Deno の変化のキーとなったブログポスト

---
class: center middle

[Big Changes Ahead for Deno](https://deno.com/blog/changes) - 8月

<img src="./assets/big-changes.jpg" align="center" width="700" />

---

<img src="./assets/hinosawa.jpg" align="right" width="150" />

# 話す人

日野澤歓也 twitter @kt3k

- <small>Web エンジニア (2009 - 現在)</small>
- <small>Deno Land, ソフトウェアエンジニア (2021 - 現在)</small>

<small>2018年(プロジェクト初期)から OSS である Deno にコントリビュート。2020年作者に誘われ Deno Land に転職。現在はフルタイムで Deno と Deno Deploy を開発中</small>

---
本日のアジェンダ

- Deno のおさらい
- Big Changes in 2022

---
class: middle center

Deno とは

---
class: middle center

DX (開発体験) にフォーカスした<br />JavaScript runtime

---
DX にフォーカスした JavaScript runtime

- ビルトイン開発ツール
  - `deno lint`
  - `deno fmt`
  - `deno test`, etc

cf. `prettier` `eslint` `jest` `vitest`

---
DX にフォーカスした JavaScript runtime
- TypeScript ビルトイン
  - 設定不要、インストール不要

---
DX にフォーカスした JavaScript runtime

- 整理されたモジュール機構
- Node, Bun
  - 🤷 CJS <-> ESM interop
  - 🤷 `.cjs` `.mjs` `.cts` `.mts`
  - 🤷 `{ "type": "module|commonjs" }`
- Deno
  - ✅ ESM only
  - ✅ .ts .js

---
class: middle center inverse

<img src="./assets/jsts.jpg" />

---
DX にフォーカスした JavaScript runtime

- サプライチェーン攻撃に対する防御機構

<img src="./assets/perm.png" width="750" />

--

<small>内部で V8 のサンドボックス機構を利用している</small><br />
<small>詳細は公式ドキュメント [Permission ページ](https://deno.land/manual@v1.27.2/basics/permissions) 参照</small>

---
DX にフォーカスした JavaScript runtime

- Web 互換 API
  - `fetch()`
  - TypedArray - `Uint8Array` etc
  - `prompt()`

--

<br />
<br />
<small>ブラウザで使える知識と同じ知識で Deno のコードが書ける</small><br />

--
<small>Deno で使える Web API 一覧はブログ記事 [list of every web API](https://deno.com/blog/every-web-api-in-deno) 参照</small>

---
class: middle center

Deno は JS runtime のあるべき姿を模索している

---
class: center middle

[Big Changes Ahead for Deno](https://deno.com/blog/changes)

<img src="./assets/big-changes.jpg" align="center" width="700" />

---
Big Changes

Deno に今後起こる3つの変化

- npm 互換性
- パフォーマンス向上
- DX 向上 (主にモジュール検索性)

---
class: middle center

npm 互換性

---
npm 互換性

npm モジュールとの互換性を導入すると宣言 - 8月
--

- `npm:` specifier の導入

--
  - Deno v1.25 でリリース

--
  - Deno v1.28 で安定化

---
パフォーマンスの向上

- パフォーマンスだけを専門的にやるチームが発足
- Deno.serve (コードネーム Flash) API が `--unstable` フラグ付きでリリース
  - 既存の Deno.serveHttp よりも圧倒的に速い
- Bun の HP に載っている 3つのベンチマークは実は結構変わっている。
  - 単なる HTTP、単なる FFI では Bun は Deno に勝てなくなってきている

---
DX 向上

- Deno はモジュールの検索性が悪いという問題があった。
  - たとえば oak という Deno 界でかなり使われているモジュールがある
  - Deno レジストリで oak を検索すると何故か 2ページ目に oak 本体が表示されていた
- 人気順を加味したモジュール検索を実装
- 更にシンボル検索を実装
  - Deno 本体、標準モジュール、3rd パーティモジュールのすべての公開 API の中から横断的に機能を検索出来るようになった

---

以上
