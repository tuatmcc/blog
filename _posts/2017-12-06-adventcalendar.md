---
layout: post
title: Jekyllチュートリアル
---

### はじめに
これは[MCC Advent Calendar](https://adventar.org/calendars/2421)6日目の記事です。  
前回はGEN52462138さんによる[ディスプレイなしでラズパイを操作する](http://shangtian.hatenablog.com/entry/2017/12/05/064136)でした。  

こんにちは、部員のepcnt19です。  
MCCではサーバ担当で、主に部内インフラ系を担当しています。  
本記事では、当ブログで使われているJekyllの簡単な使い方について書いていきます。  
Jekyllの使い方(主に投稿方法)がわからない部員の方向けの導入記事だと思って下さい。

### Jekyllとは
JekyllとはRuby製のシンプルな静的サイトジェネレータです。Markdown形式のテキストを変換し、HTMLファイル一式を出力してくれます。詳細は[Jekyllの公式ページ](https://jekyllrb-ja.github.io/docs/home/)を参照してください。  
JekyllのいくつかのテンプレートとMarkdownがわかっていれば最低限記事は書けます。  

Markdownの入門については以下を参照すると良いかと思います。  
* [Makdown記法入門 - ドットインストール](https://dotinstall.com/lessons/basic_markdown_v2)

今回はJekyllのレイアウトや変数については扱いませんので、詳細は以下を参照すると良いかと思います。
* [Jekyll入門 - ドットインストール](https://dotinstall.com/lessons/basic_jekyll)

また、GitHub Pagesを使うため、当然ながらGitの知識も必要となります。ただし、記事投稿に関してはcommit、add、pushなどの最低限基本的なことができれば問題ありません。


### 環境構築
今回は以下の環境で進めていきます。  

```
OS  Linux(Ubuntu 16.04.2 LTS)
Ruby 2.4.2p198
rbenv 1.1.1
github-pages 171
jekyll 3.6.2
```
JekyllはRuby製のため、Rubyがインストールされている必要があります。今回はRubyのバージョン管理ツールであるrbenvを使ってインストールします。  

github-pagesとはGithub Pagesが使用しているJekyllの関連パッケージで、これをインストールするとJekyllもインストールされます。

### rbenvのインストール
はじめに、rbenvの依存パッケージをインストールし、rbenvをcloneします。
```
$ sudo apt-get install git build-essential libssl-dev
$ git clone https://github.com/sstephenson/rbenv.git ~/.rbenv
$ git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
```
次に、~/.bashrcを編集し、下記を追記します。
```
$ vim ~/.bashrc
```
```
#最下行に下記を追記
export PATH="$HOME/.rbenv/bin:$PATH"
eval "$(rbenv init -)"
```
```
$ source ~/.bashrc
```

### Rubyのインストール
rbenvを使って、Rubyをインストールします。インストールにはしばらく時間がかかります。  
インストール完了後にBundlerもインストールしておきます。

```
$ rbenv install 2.4.2
$ rbenv global 2.4.2
$ gem install bundler
```

### github-pages(Jekyll)のインストール
今回はバージョン171をインストールします。これは当ブログのバージョンと合わせるためです。
```
$ gem install github-pages -v 171
```
以上でJekyllがインストールされました。通常はこの後、`jekyll new (プロジェクト名)`のようにしてjekyllの新規プロジェクトを作成するのですが、今回は既存プロジェクトの記事更新をしていきます。

### 記事の更新
#### ローカルサーバの起動
既存ブログのプロジェクトをローカル内に取り込みます。
```
$ git clone https://github.com/tuatmcc/blog.git
$ blog
$ bundle install
```
Jekyllのローカルサーバを起動します。ブラウザで`http://127.0.0.1:4000`(ローカルホストの4000番ポート)にアクセスするとブログを参照できます。プレビューするときはブラウザから確認しましょう。
```
$ jekyll server --baseurl '' --watch
WARN: Unresolved specs during Gem::Specification.reset:
      jekyll-watch (~> 1.1)
WARN: Clearing out unresolved specs.
Please report a bug if this causes problems.
Configuration file: /home/user/mcc/blog/blog/_config.yml
            Source: /home/user/mcc/blog/blog
       Destination: /home/user/mcc/blog/blog/_site
 Incremental build: disabled. Enable with --incremental
      Generating... 
     Build Warning: Layout 'none' requested in feed.xml does not exist.
                    done in 0.646 seconds.
 Auto-regeneration: enabled for '/home/user/mcc/blog/blog'
  JekyllAdmin mode: production
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.
```

#### 記事の設置
記事のMarkdownファイルを`_posts`以下に以下のようなファイル名前で設置します。  
`(名前) yyyy-mm-dd-article_name.md`  
`(例) 2017-12-06-test.md`  

Markdownファイル中の先頭に以下のような内容を追加します。これはJekyllのレイアウトや記事タイトルを指定するためのものです。
```
---
layout: post
title: (記事タイトル)
---
```


#### 記事の投稿
ブラウザでプレビューしながら、問題がなさそうであれば記事をリモートのブログに反映させます。
```
$ git add .
$ git commit -m "Write commit message"
$ git push
```

#### その他
MCCのブログに記事投稿するためには、Githubアカウント及びOrganizationアカウント参加申請が必要です。
Organization申請については部会等で担当者に聞いて下さい。  
現在、これらのローカル環境構築やGit(Hub)のアカウント/知識がなくても良いようにブログ投稿サービスを開発しています。
詳細をお待ちください。

## おわりに
サーバ担当としては、Jekyllの方がWordPressより管理が楽で助かります。  
次回のAdvent Calendarは、Um6ra1さんによる[USBﾄﾞﾗｲﾊﾞを書いてみよう ～RTL2832uでLチカ～](https://adventar.org/calendars/2421#list-2017-12-09)です。
