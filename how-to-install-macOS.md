## 【macOS】 PostgreSQLおよびpgAdminのインストール
### 1. Homebrewのインストール
パッケージマネージャの[Homebrew](https://brew.sh/index_ja)をインストールします．  
すでにインストールしている人は飛ばしてください．  
#### 1-1 Launchpad->その他->ターミナル を起動
#### 1-2 XcodeのCommand Line Toolsをインストール
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

#### 1-3 Homebrewをインストール
以下のスクリプトをターミナルに貼り付けて実行する．
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
### 2. PostgreSQLのインストール
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
以下のコマンドをターミナルに貼り付けてパスを設定する．  
```
echo 'export PGDATA="/usr/local/var/postgres"' >> ~/.bash_profile
```
データベースを初期化  
```
initdb /usr/local/var/postgres -E utf8
```
### 3. pgAdmin4のインストール
GUIで管理できるツールであるpgAdmin4をインストールする．  
以下のコマンドをターミナルに貼り付けて実行する．
```
brew cask install pgadmin4
```

### 参考サイト
* [macOS 用パッケージマネージャー — Homebrew](https://brew.sh/index_ja)
* [Homebrew のインストールと基本的な使い方 - yu8mada](https://yu8mada.com/2018/04/12/homebrew-s-installation-and-basic-usage/#article-title)
* [pgAdmin - PostgreSQL Tools](https://www.pgadmin.org/)
* [【Mac&Homebrew】PostgreSQLのインストール方法とpgAdmin4を使った接続方法を丁寧に説明！ | 全人類がわかる統計学](https://to-kei.net/db/postgre-mac-install/)
