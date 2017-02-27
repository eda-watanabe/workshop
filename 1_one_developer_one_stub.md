# 1人の開発者に1つのスタブ環境
## Overview
アプリ開発には通信処理による非同期の実装が必ずと言っていいほどあり、サーバーサイドの実装も必須であることが多い。サーバーの実装がアプリの実装よりも先行していればアプリの実装が非同期の処理を後回しにすることはないが、そのケースはない。
サーバーの実装もアプリと並行しているケースが弊社の開発スタイルだ。そこで、仕様書に従ったapiのstubを用意することで、非同期の処理を後回しにせずに実装するのが今日の弊社の開発スタイルだが、  
apiの返却値によって異なる処理をする場合ここで一つの問題がある。
```
stubが１つしかないと他の開発者にも影響がでる
```
stubの雛形を共有し各自で自分自身のstub環境を構築することでこの問題を解決する。

## Herokuにstub環境を構築する with PHP

### Herokuとは
https://www.heroku.com/
```
Paasと呼ばれるサービスでアプリケーションのプラットフォーム
```
Paas -> プラットフォーム構築（アプリケーション公開）にかかる数々の作業を代行

### サポートしている言語
- Ruby
- Java
- Python
- Clojure
- Scala
- Node.js
- [PHP](https://devcenter.heroku.com/categories/php)

### メリット
- 拡張機能（アドオンが充実)
 - https://elements.heroku.com/addons
- スケールアウト（パフォーマンス向上が簡単）

### アカウント作成

### Setup
- php
```
$ php -v
```
- [comporser](https://getcomposer.org/download/)  
Dependency Manage for PHP
``` 
& composer -V 
```
- [git](https://git-scm.com/)
```
$  git --version
```
- [Visial Studio Code](https://code.visualstudio.com/)  
gitがつかえるから便利

[Heroku CLI](https://devcenter.heroku.com/articles/getting-started-with-php#set-up)をインストールして`heroku`コマンドを使えるようにする

### login
```
$ heroku login
```

### herokuアプリ作成
フォルダを作成し、`index.php`と`composer.json`(空でok)を作成

index.php
```php
<?php
echo "Hello,Heroku World!";
```
herokuアプリ作成
```
$ heroku create
```

### デプロイ
```
$ git push heroku master
```
ブラウザで開く
```
$ heroku open
```

END

