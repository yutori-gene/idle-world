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

`main` への push で GitHub Actions が `site/` の中身を `gh-pages` ブランチへ publish し、Pages がそれを配信する（`.github/workflows/pages.yml`）。
手動で流すなら Actions → Deploy overview to GitHub Pages → Run workflow。
