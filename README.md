# memoApp
好きな作品をメモに残すことができるwebアプリを作成しました。

<img width="400" alt="memoApp1" src="./memoApp1.png">

## 目次
- [使い方](#使い方)
- [技術スタック](#技術スタック)
- [実行](#実行)
- [今後](#今後)

## 使い方
- 「新規投稿」から新しくメモを投稿することができます。
  
   <img width="400" alt="memoApp1" src="./memoApp2.png">

- これまでの投稿は投稿一覧から見ることができます。
  
  <img width="400" alt="memoApp1" src="./memoApp3.png">

- 投稿は後から編集することや削除することも可能です。
  
  <img width="400" alt="memoApp1" src="./memoApp4.png">


## 技術スタック
- Ruby 3.1.4
- Ruby on Rails 7.0.4.3

## 実行
サーバーの起動
```bash
rails server
```
    
アクセス先： http://localhost:3000/　

## 参考
* `rails new アプリケーション名` でアプリケーションの土台が作れる  
* bundle installでgemをinstall

## ファイルの構成 ##

/app  railsのメインフォルダ
---

#### /assets ####
/images(画像)や/stylesheets(CSS)など、ページを装飾するものをまとめたフォルダ

#### /controllers ####

MVCのCの部分。変数はここで扱う。
`rails g controller hoges`のコマンドを叩くと、このフォルダにhoges_controller.rbが作成される

#### /models ####
MVCのMの部分。データベースとのやり取りや制約などを記述するモデルをまとめたフォルダ。`rails g model Hoge`のコマンドを叩くと、このフォルダにHoge.rbが作成

#### /views ####
MVCのVの部分。ページの見た目を作るためのフォルダ。`rails g controller hoges index` とコマンドを打てば該当のファイルにindex.html.erbが作成
views/layouts/application.html.erbに共通のHTMLを書いておくことができる

#### /helpers ####
helper:viewをシンプルにするために、ちょっとした処理をやりたい時に使うメソッド

/bin
---
サーバを起動したり、テストをしたり、アプリケーションを管理する様々なスクリプトファイルをまとめるフォルダ。各プロジェクトのRailsのバージョンが違っていた場合、bin/rails sと/binを指定してコマンド実行するとそのバージョンでのコマンドで実行される

/config 
---
RailsやルーティングやDBなど、Railsの様々な設定ファイルをまとめてあるフォルダ
#### routes.rb ####
取得したURLを適切なコントローラー内のアクションなどに割り当てるためのルーティングファイル。
##### Routing Errorの原因はだいたいここ。 #####
rails routesで割り当てているルーティングの一覧が見れる。

/db  
---
データベース関連の情報をまとめたフォルダ。デフォルトだとseeds.rbしかない。
#### /migrate ####
モデル作成時やrails g migration hogehogeでマイグレーションファイルがこのファイルの直下に作成される。
rails db:migrateを実行すると生成したテーブルやカラムなどがマイグレーションファイルを参考にデータベースへ内容が保存される

#### schema.rb
rails db:migrate実行後に生成される、実行結果（実際にデータベースに保存されているテーブル等）が反映されているファイル

#### seeds.rb
既存のテーブルにデータを格納するために設定するファイル。
記述し、rails db:seedを実行するとデータベースにデータが格納される


/lib
---
自作のモジュールを置く場所。
ここにモジュールを置いて、requireで呼び出す。

/log
---
いわゆるログファイル。デフォルトでは中身はない。
logger.debugを使うことで、log/development.logにlogを出力できる

/public
---
404.htmlなどRailsを使用しない静的ページや画像を格納する。

/temp 
---
一時ファイルを保存するためのファイルをまとめたフォルダ

/vendor
---
vendorは自分が開発しているものではないサードパーティのライブラリ(jsフレームワークやcssフレームワークなど)を格納する場所

Gemfile
---
現在のアプリケーションで使うgemをまとめているファイル。
このファイルに追加したいgemを記入し、bundle installを実行するとgemがinstallされる

Gemfile.lock
---
Gemfileを元に依存関係にあるgemのバージョンと取得先が記録される。
実際にインストールしたgemのリストという認識。
bundle installやbundle updateで更新される

参考：
* https://qiita.com/len_crow/items/7127b31d68197983de87
* ProgateのRuby on railsの講座
