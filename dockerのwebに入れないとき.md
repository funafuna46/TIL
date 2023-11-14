### dockerのwebコンテナに入れないときの解決方法
#### 状況
- ```docker compose exec web bash```コマンドを使用してwebコンテナに入ろうとした時、```service "web" is not running container #1```とエラーが発生する
- ```docker ps```コマンドで確認すると、webコンテナが存在しない

#### 解決方法
1. コンテナのログを確認するため、```docker logs コンテナ名```でログを確認する
2. syntax error等原因が分かるので、コードを修正
3. ```docker compose restart```でdockerを再起動
4. ```docker ps```でwebコンテナが起動しているか確認できる
