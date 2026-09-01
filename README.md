# idle-world

[yutori-gene/idle](https://github.com/yutori-gene/idle) のワールド定義データ（`world/list` の CSV）の**現状一覧ビュー**を公開する。

<https://yutori-gene.github.io/idle-world/>

アイテム905種・アクション973本を、カテゴリ／グループでの絞り込み・全文検索・列ソートで眺められる1枚もの。
データは HTML に埋め込まれているので、単体で開ける。

## 更新のしかた

このリポジトリのファイルは**生成物**で、手で編集しない。源泉は `idle` 側にある。

```
idle/world/list/*.csv          源泉（ワールド定義）
  → idle/world/tool/overview.py で生成
idle/world/overview.html       生成物
  → このリポジトリの site/index.html へコピーして push
```

**公開は自動で走らない。指示があったときだけ流す。**
`main` に push しただけでは Pages は古いままで、公開のたびに手でワークフローを発火させる。

> Actions → **Publish overview to gh-pages** → Run workflow（`main`）

発火すると `site/` の中身が `gh-pages` ブランチへ force push され、Pages がそれを配信する（`.github/workflows/pages.yml`）。
つまり `main` は「次に公開する内容の置き場」で、`gh-pages` が「いま公開されている内容」になる。

## 初回だけ必要な設定（リポジトリ管理者）

Pages サイトの**新規作成だけは Actions の `GITHUB_TOKEN` で行えない**ので、最初の1回だけ手で有効化する。

> Settings → Pages → Build and deployment
> Source: **Deploy from a branch** ／ Branch: **`gh-pages`** ／ **`/ (root)`** → Save

以降は上の「更新のしかた」どおり、ワークフローを手で発火させたときだけ反映される。
