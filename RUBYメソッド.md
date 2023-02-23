# RUBYメソッド

### ◆mapメソッド  
 配列の要素の数だけブロック内で処理を繰り返して、新しい配列を返します。  

空の配列を用意して、他の配列を順番にループ処理をした結果を空の配列に入れる処理は、mapメソッドに置き換えることが出来ます！

mapメソッドは返り値が新しい配列になるだけで、元の配列は変わっていないそのままの値になるが、map!メソッドは元の配列の値そのものを上書きするので使い方に注意する。

  * 例 

    * 配列.map { |変数| 実行する処理 } 
  ```ruby
    numbers = [10, 20, 30, 40]
    new_numbers= numbers.map { |n| n * 2 }
    new_numbers 
    => [20, 40, 60, 80]

   ```


  * 実行する処理が複数行に渡る場合  
      配列.map do |変数|  
        実行する処理  
      end  

  ```ruby

  配列.map { |変数| 実行する処理 }
    numbers = [10, 20, 30, 40]
    new_numbers= numbers.map { |n| n * 2 }
    new_numbers 
    => [20, 40, 60, 80]

   ```


データベースから特定の値だけ配列にする方法
mapメソッドは、Railsでテーブルから特定のカラムの値を取得したいときに便利です。

usersテーブルの全ユーザーの名前を取得するとき、mapメソッドを使えば簡単に取得する事が出来ます。

ユーザーの名前だけ配列にする場合-->
users = User.all
users.map { |user| user.name }

=> ["Jacob", "Jackson", "Noah", "Lucas", "Sophia", "Chloe", 





mapメソッド内にメソッドを使用する方法
mapメソッドは、ブロック内でメソッドを利用することで更に細かい条件の配列を作り出す事が出来ます。

今回は20歳以上だったら値を返すfilter_r20_arrメソッドを使って解説していきます。

引数(age)に渡された値が20以上だったらageを返すメソッド-->
def filter_r20_arr(age)
  age if age  >= 20
end
年齢がバラバラに入ったagesの配列の要素をr20_limited?メソッドの引数(age)に入れることによって、返り値は20歳以上の要素の配列にしています。

mapメソッド内にfilter_r20_arrメソッドを使用する-->
ages = [9, 11, 23, 45, 66, 12, 77]
filtered_r20_arr =  ages.map { |age|  filter_r20_arr(age) }
=> [nil, nil, 23, 45, 66, nil, 77]

filtered_r20_arr.compact
=> [23, 45, 66, 77]











  mapメソッドの省略した書き方
mapメソッドは、下記の３つの条件に合えば、ブロックを渡す代わりに&:メソッド名を使って省略して書くことが出来ます。

ブロックの引数が１つであること
ブロックで呼び出すメソッドに引数がないこと
ブロック引数に対して、メソッドを呼び出すこと以外の処理がないこと
mapメソッドの省略した書き方 -->
# 通常の書き方
["RUBY", "PHP", "JAVA"].map { |s| s.downcase }
=> ['ruby', 'php', 'java']

# 省略した書き方
["RUBY", "PHP", "JAVA"].map(&:downcase)
=> ["ruby", "php", "java"]


Hashでmapメソッドを使う方法
mapメソッドは、配列だけではなくHashに対しても使用することができます。
キーがkeyに代入され、値がvalueに代入されます。

irb | Hashにmapメソッドを使う例
irb(main):001:0> h = { BANANA: 100, ORANGE: 200, MELON: 300 }
=> {:BANANA=>100, :ORANGE=>200, :MELON=>300}

irb(main):002:0> h.map { |key, value| [key.downcase, value] }
=> [[:banana, 100], [:orange, 200], [:melon, 300]]
ただし、返り値はハッシュではなく、配列になるので注意してください。返り値を配列ではなくHashにする場合は、to_hメソッドを使用します。

irb | 配列からHashに変換する
irb(main):003:0> h.map { |key, value| [key.downcase, value] }.to_h
=> {:banana=>100, :orange=>200, :melon=>300}





   collectメソッドは、mapメソッドと全く同じ動作をするメソッドです。

irb | collectメソッドを使う場合
irb(main):009:0> numbers = [10, 20, 30, 40]
=> [10, 20, 30, 40]
irb(main):010:0>new_numbers= numbers.collect { |n| n * 2 }
=> [20, 40, 60, 80]