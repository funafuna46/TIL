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
