# ① myappをユーザー直下に解凍します
![image-20191119101214129.png](/knowledge/open.file/download?fileNo=51)
<br><br>
# ② 配置したmyappフォルダに移動します
```
cd C:\Users\myapp
```
<br><br>
# ③ 
```
docker-compose run web rails new . --force --no-deps --database=mysql
```
→実行するとmyappは以下にファイルが増えます
#### (1)Pulling db （mysql）
　　→mysqlのDBを構築
#### (2)Pulling from library/ruby
　　→rubyの環境を構築
→「Bundle complete!」が出たら完了！
<br><br>
# ④ DBの設定を変更するため、一度コンテナを停止します
```
docker-compose down
```
<br><br>
# ⑤ DBの向きを変更します
C:\Users\myapp\config\database.yml　を配布したファイルでファイルごと上書きします
<br><br>
# ⑥ ファイルを配置します
C:\Users\myapp\mysql-confd　に　ファイル（default_authentication.cnf）を配置します
<br><br>
# ⑦ コンテナをビルドします
```
docker-compose build
```
→「Successfully built ●●●●●●●●●」が出たら完了！
<br><br>
# ⑧ 先にDBを起動します
```
docker-compose up -d db
```
<br><br>
# ⑨ webを起動します
```
docker-compose run web rake db:create
```
<br><br>
# ⑩ up　します 
```
docker-compose up -d
```
<br><br>
![image-20191120110345036.png](/knowledge/open.file/download?fileNo=54)
<br>
# ★チェックポイント★
正常に起動しているかを確認
```
docker ps -a
```
![image-20191120105738281.png](/knowledge/open.file/download?fileNo=52)
↑のように「myapp_web」と「mysql」のコンテナがupしていればOK！
<br>
![image-20191120110345036.png](/knowledge/open.file/download?fileNo=54)
<br><br>
# ⑪ bashで操作するために、コンテナへログイン
```
docker exec -it CONTAINER_ID bash
```
→`CONTAINER_ID`は、全員別のIDが振られています。
![image-20191120105929084.png](/knowledge/open.file/download?fileNo=53)

<br><br>
# ⑫ 以下を、１行ずつ実行
```
rails g model Task title:string context:string level:integer
```
```
rails db:migrate
```
```
rails g controller Tasks
```
<br><br>
# ⑬ myapp\app\controllers　配下の以下のファイルを編集する
対象ファイル：
```

```
<br><br>
# ⑭ myapp\db　配下の以下のファイルを編集する
対象ファイル：seeds.rb
```

```
<br><br>
# ⑮ DBにデータを送る
```
rails db:seed
```
<br><br>
# ⑯ myapp\config　配下の以下のファイルを編集する
対象ファイル：routes.rb
```

```
<br><br>
# ⑰ 以下を、１行ずつ実行
```
touch app/views/tasks/index.html.erb
```
```
touch app/views/tasks/show.html.erb
```
```
touch app/views/tasks/new.html.erb
```
```
touch app/views/tasks/edit.html.erb
```
<br><br>
# ⑱ 　配下の以下のファイルを編集する
対象ファイル：index.html.erb
```

```
<br><br>
# ⑲ 以下に接続して確認！
```
http://localhost:3000/
```
![image-20191121003744232.png](/knowledge/open.file/download?fileNo=56)
<br>
このような画面が表示されたら完成！