## enumについて
Railsは```enum```を使用すると、それぞれの状態に対して述語メソッドを自動的に提供する。<br>
例えばモデルに以下のようなenum宣言がある時、
```
class Article < ApplicationRecord
  enum state: { draft: 0, published: 1, publish_wait: 2 }
  # ...
end
```
この定義により、Articleオブジェクトに対して```draft?```メソッドを呼び出すと、その記事のstate属性が```0```であるかどうかをチェックできる。<br>
```published?```や```publish_wait?```メソッドも利用できる。

以下のようにステータスの絞り込みでもwhere句を使用せず簡潔に書くことができる。
```
# NG
article.state = 'publish_wait'
Article.where(state: :publish_wait)

# OK
Article.publish_wait
```
<br>
<br>
<br>

### enum宣言をした時に自動的に追加されるメソッドまとめ
以下のようにenumが定義されている場合：
```
enum state: { draft: 0, published: 1, publish_wait: 2 }
```
Railsは以下の種類のメソッドをArticleモデルに追加する：

1. スコープ（Scope）<br>特定の状態を持つレコードを簡単に取得できる
```
Article.draft、 Article.published、 Article.publish_wait
```
2. 値のセットメソッド<br>
レコードのstateを特定の値に設定するメソッド。これらのメソッドを使用すると、stateを対応する値に更新してデータベースに保存する。
```
article.draft!、 article.published!、 article.publish_wait!
```
3. プレディケートメソッド（述語メソッド）<br>
レコードのstateが特定の値かどうかを確認するためのメソッド。これらのメソッドは、対応する値が設定されている場合にtrueを返す。
```
article.draft?、 article.published?、 article.publish_wait?
```
