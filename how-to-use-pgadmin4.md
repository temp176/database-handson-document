## 0. 【macOSの場合】postgreSQLサーバを起動
以下のコマンドをターミナルに貼り付けてpostgreSQLサーバを起動する．  
※Windowsの場合は自動で起動すると思います．　　
```
postgres
```
もしくは  
```
postgres -D /usr/local/var/postgres
```

## 1. pgAdmin4の起動
### Windowsの場合
スタートメニューから起動してください．  
![](https://itsakura.com/wp-content/uploads/2019/03/pgadmin4-db-create1.png)  
### macOSの場合
Launchpad->pgAdmin4  
もしくは  
Finder->アプリケーション->pgAdmin4.app  
から起動してください．  
  
また，起動時にパスワードの設定を求められると思うので入力してください．  （覚えておいてください）
<img src="https://github.com/temp176/database-handson-document/blob/master/image/pgadmin-password.png" width="500">

## 2. 使い方
[こちらのサイト](https://itsakura.com/pgadmin4-db-create)を一部参考・引用しています．
### 2-1 サーバの作成
#### 「Servers」を右クリックして「Create」->「Server」をクリックします．  
<img src="https://itsakura.com/wp-content/uploads/2019/03/pgadmin4-db-create2.png" width="500">
  
#### 「Name」にサーバー名を入力し．作成するサーバーが所属するサーバーグループ「Server group」を選択します．  
完了後，「Connection」タブをクリックします．  
<img src="https://itsakura.com/wp-content/uploads/2019/03/pgadmin4-db-create3.png" width="500">
 
#### Connectionタブ
「Host name/address」には「127.0.0.1」または「localhost」を指定する．  
「Password」にはサーバーに接続する際のパスワードを入力する．  
「Save password」にチェックを入れると，このサーバーに再接続した時にパスワードを手入力せずに接続できる．  
「Save」を押して完了．  
<img src="https://itsakura.com/wp-content/uploads/2019/03/pgadmin4-db-create4.png" width="500">

#### macOSで「FATAL: role "postgres" does not exist」となる場合  
「Username」を自分の名前にしてみる．  
  
##### 名前の確認方法
1. サーバを起動しているターミナルとは別のターミナルを開く
2. ターミナルで```psql -l```を実行する
3. 「Owner」の列に書かれている名前を「Username」としてみる

### 2-2 データベースの作成
#### サーバーを右クリックして「Create」→「Database」をクリックする
<img src="https://itsakura.com/wp-content/uploads/2019/03/pgadmin4-db-create10.png" width="300">

#### 「Database」にデータベース名を入力し、Saveボタンを押す
<img src="https://itsakura.com/wp-content/uploads/2019/03/pgadmin4-db-create11.png" width="300">

#### データベースが作成されます
<img src="https://itsakura.com/wp-content/uploads/2019/03/pgadmin4-db-create12.png" width="300">

### 2-3 テーブルの作成およびSQL文の実行
#### 作成したデータベースを右クリックして「Query Tool」を選択
<img src="https://github.com/temp176/database-handson-document/blob/master/image/sql1.png" width="300">

#### 「Query Editor」タブにSQL文を入力
例えば以下のテーブルを作成するSQL文を入力する．
```
CREATE TABLE Test(ID bigint PRIMARY KEY, col1 varchar, col2 varchar, col3 varchar);
```
#### その後雷マークのボタンを押すことでSQL文を実行． 
<img src="https://github.com/temp176/database-handson-document/blob/master/image/sql2.png" width="500">

#### 「Schemas」->「Tabeles」->「Test（作成したテーブル名）」を右クリックし，「Viwe/Edit Data」の「All Rows」を選択
<img src="https://github.com/temp176/database-handson-document/blob/master/image/sql3.png" width="500">

#### テーブルの内容を確認することができる
<img src="https://github.com/temp176/database-handson-document/blob/master/image/sql4.png" width="500">

#### 同様に他のSQL文も実行できる
例えば以下のSQL文を「Query Editor」タブに入力し実行すると
```
INSERT INTO test(ID, col1, col2, col3) VALUES (1, '一列目', '二列目', '三列目')
```
テーブルにデータが追加されることがわかる  
<img src="https://github.com/temp176/database-handson-document/blob/master/image/sql5.png" width="500">

### その他
* CREATE VIEWなどで作成したViewは「Tables」の3つ下にある「Views」からテーブル内容と同様の方法で確認できます
* SQL文の実行が成功したにも関わらず結果が更新されない場合は，「Tables」などを右クリックした際に出てくる「Refresh...」などを試してみる


## 参考サイト
* [PostgreSQL pgAdmin 4の使い方(起動からデータ参照) | ITSakura](https://itsakura.com/pgadmin4-db-create)
* [PostgreSQLでSQL実行までのチュートリアル - DEV Community 👩‍💻👨‍💻](https://dev.to/programmingmonky/postgresqlsql-3dja)
