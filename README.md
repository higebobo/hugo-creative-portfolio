# README

## セットアップ

サイト作成

```shell
hugo new site hugo-creative-portfolio
```

レポジトリ初期化

```shell
cd hugo-creative-portfolio
git init
echo '*.bak' >> .gitignore
echo '*~' >> .gitignore
echo '*.orig' >> .gitignore
echo 'public' >> .gitignore
```

テーマ設定

```shell
cd themes 
git submodule add https://github.com/kishaningithub/hugo-creative-portfolio-theme.git
```

サイト設定

```shell
cd hugo-creative-portfolio
cp -pr ./themes/hugo-theme-dream/exampleSite/* .
```

config.toml

```toml
baseURL = "https://higebobo.github.io/hugo-creative-portfolio/"
title = "Hugo Creative portfolio"
theme = "hugo-creative-portfolio-theme"
languageCode = "ja"
#publishDir = "docs"
```

> github pagesやnetlifyで使う場合はbaseURLのプロトコルはhttpsにすること

archetypesの設定

archetypes/portfolio.md

```markdown
+++
image = "img/portfolio/gravity-paper.jpg"
showonlyimage = true
date = {{ .Date }}
title = "{{ replace .Name "-" " " | title }}"
draft = true
weight = 10
+++
```

Githubレポジトリ作成後

```shell
git remote add origin git@github.com:higebobo/hugo-creative-portfolio.git
hugo
git add -A
git commit -m 'init'
git push -u origin master
```

## Github Actionsの利用

* .github/workflows/gh-pages.yamlを作成
    * ソースはmasterブランチ
    * 出力はpublicフォルダの内容をgh-pagesブランチ
        * Github>Settings>Gighub Pages>Source>gh-pages branch

## 既存のレポジトリからクローンする場合

```shell
git clone git@github.com:higebobo/hugo-creative-portfolio.git higebobo-creative-portfolio
cd higebobo-creative-portfolio
git submodule update --init --recursive
```

## 使い方

### 投稿

新規ポートフォリオ

```shell
hugo new portfolio/work12.md
content/portfolio/work12.md created
```

編集

```shell
vi content/portfolio/work12.md
```

下書きモード解除

```shell
vi content/posts/2020/05/helloworld.md
draft: false
```

公開(githubにプッシュ)

```shell
make deploy
```

## Link

* [Hugo Creative Portfolio Theme \| Hugo Themes](https://themes.gohugo.io/hugo-creative-portfolio-theme/)
