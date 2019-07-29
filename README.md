# database-handson-document
## PostgreSQLおよびPgAdminのインストール
### macOSの場合
#### 1. Homebrewのインストール
パッケージマネージャの[Homebrew](https://brew.sh/index_ja)をインストールします．  
すでにインストールしている人は飛ばしてください．  
##### 1-1 Launchpad->その他->ターミナル を起動
##### 1-2 XcodeのCommand Line Toolsをインストール
以下のコマンドをターミナルに貼り付けて実行する．
```
xcode-select --install
```
インストールが終了したら，以下のコマンドをターミナルに貼り付けてインストールが成功したかを確認する．
```
xcode-select -v
```
バージョンが表示されたらOK．  
表示例：  
```
xcode-select version 2354.
```

##### 1-3 Homebrewをインストール
以下のスクリプトをターミナルに貼り付けて実行する．
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
#### 2. PostgreSQLのインストール
以下のコマンドをターミナルに貼り付けて実行する．
```
brew update
brew install postgresql
```
インストールが終わったら以下のコマンドをターミナルに貼り付けてインストールが成功したかを確認する．
```
postgres --version
```
表示例：
```
postgres (PostgreSQL) 11.3
```
#### 3. PgAdmin4のインストール
GUIで管理できるツールであるPgAdmin4を以下のURLからインストールする．  
URL:[https://www.pgadmin.org/](https://www.pgadmin.org/)  
  
##### 3-1 Downloadリンクをクリック  
![](https://github.com/temp176/database-handson-document/blob/master/image/pgadmin1.png)
  
##### 3-2 OSを選択  
![](https://github.com/temp176/database-handson-document/blob/master/image/pgadmin2.png)

##### 3-3 最新バージョンを指定  
![](https://github.com/temp176/database-handson-document/blob/master/image/pgadmin3.png)

##### 3-4 実行ファイルをダウンロードしてインストール
![](https://github.com/temp176/database-handson-document/blob/master/image/pgadmin4.png)

#### 参考サイト
* [macOS 用パッケージマネージャー — Homebrew](https://brew.sh/index_ja)
* [Homebrew のインストールと基本的な使い方 - yu8mada](https://yu8mada.com/2018/04/12/homebrew-s-installation-and-basic-usage/#article-title)
* [pgAdmin - PostgreSQL Tools](https://www.pgadmin.org/)

### Windowsの場合
