## Docker環境でgemをインストールする手順
#### 1. コンテナ内に入る
```
docker exec -it コンテナ名 bash
```
コンテナ名は```docker ps```で確認できる

#### 2. Gemfileにgemを追記
#### 3. コンテナ内で```bundle install```を実行
