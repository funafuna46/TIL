### better_errorsを使う方法
1. Gemfileに追記
```
group :development do
  gem 'better_errors'
  gem 'binding_of_caller'
end
```
2. ```bundle install```コマンドを実行

3. Dockerを使用している場合、以下を追加

```
# app/config/environments/development.rb
BetterErrors::Middleware.allow_ip! "0.0.0.0/0"
```
