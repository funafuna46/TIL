※プロジェクトのルートディレクトリで実行<br>
※Herokuはデプロイ時に自動的にマイグレーションを実行しないため、手動で実行する必要がある

### 初回設定
1. Herokuのデータベース追加コマンド
```
heroku addons:create heroku-postgresql:mini -a アプリ名
```
2. マイグレーションを実行
```
heroku run rake db:migrate -a アプリ名
```
3. seedデータをHerokuのデータベースに投入
```
heroku run rake db:seed -a アプリ名
```

### ローカルでマイグレーションファイルやseedファイル変更した場合（開発中）
1. データベースのリセット
```
heroku pg:reset DATABASE --confirm アプリ名
```
2. マイグレーションを実行
```
heroku run rake db:migrate -a アプリ名
```
3. seedデータを投入
```
heroku run rake db:seed -a アプリ名
```
