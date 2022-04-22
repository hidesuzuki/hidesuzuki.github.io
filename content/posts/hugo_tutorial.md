---
title: " HUGO導入"
date: 2022-04-22T18:07:41+09:00
draft: false 
---

# HUGOの使い始め
自身の備忘録をWordpressで構築していた。 　
管理画面にはVPNサーバーのIPアドレスのみ許容するようにしていたのだが、VPNサーバーの乗り換えに伴い、しばらく記事を更新しないでいた。  
諸々の管理が煩わしくなっていたので、今後はHUGOを使用した静的ページで運用していこうと思い、そのことに関して備忘録を残したいと思う。  
過去の記事は随時公開予定。
## 導入 
Homebrewでインストール
```
brew install
```
プロジェクトの立ち上げ
```
hugo new site PROJECT_NAME
```
記事の作成
```
hugo new posts/NAME.md
```
サーバー起動
```
hogo server
```
ドラフト記事を表示する場合は`-D`オプションをつける
```
hugo server -D
```
ビルド
```
hugo
```
## git pushでデプロイ
`.github/workflows/gh-pages.yml`を以下の通りにすると`main`ブランチの`public`配下を`master`ブランチにpushする。
```yml
name: GitHub Pages

on:
  push:
    branches:
      - main  # Set a branch to deploy

jobs:
  deploy:
    runs-on: ubuntu-20.04
    steps:
      - uses: actions/checkout@v3
        with:
          submodules: true  # Fetch Hugo themes (true OR recursive)
          fetch-depth: 0    # Fetch all history for .GitInfo and .Lastmod

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: '0.91.2'
          # extended: true

      - name: Build
        run: hugo --minify

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        if: ${{ github.ref == 'refs/heads/main' }}
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_branch: master
          publish_dir: ./public
```