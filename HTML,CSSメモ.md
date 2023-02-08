# **HTML,CSSメモ**


* floatプロパティ  
  ブロック要素を横並びにする。
  floatは「浮く」という意味、
  浮かびあがらせ、自由に配置＝横並び
  にすることができる。

  * 例  
  ```css
  .content{
    float: left;  左寄せの横並び
    (float: right;  右寄せの横並び)
  }
  .content{
    float:none;
  }
  /* 「float:none;」を使用すると、今まで横並びにする為に使用したfloatプロパティを、無かったことにできる。
  pcで横並びにした要素を、スマートフォンでは縦並びに表示させたい時に指定するとfloatが解除され、縦並びに表示させることができる。
  主にレスポンシブ対応の場面で使用します。 

  ```
<br>

 *  clear fix
  floatによる要素の重なりを防ぐCSSコード。


 例  
```HTML
 <header>header</header>
<div class="wrap">
　　<aside class="sideCol">sideCol</aside>
　　<article class="mainCol">mainCol</article>
　　<footer>footer</footer>
</div>
```
  ```css
.wrap:after {
  display: block;
  clear: both;
  content: "";
}
/* 背後でどのような処理が行われているかというと
 ・擬似要素が.wrapの最後に追加される（:after）
・clearによって擬似要素が回りこみを解除する
・擬似要素がサイドカラム・メインカラムの高さを認識し、下につく
・.wrapが子要素の高さを認識する
・footerが.wrapの下につく
という流れになる。

clearを使わないと
wrapが子要素の高さを認識できず
height:0のような状態になってしまいfooterが上に詰めてきてサイドカラム、メインカラムと重なってしまう。

.記述する場所はclear fixというクラスにして使ってもよし、floatの解除をしたい親要素に直接書いてもよし。

```

 <br>

  * floatとflexboxの違い  
  簡単に言うと
  通常の横並びはflexbox  
  テキストの回り込みがある場合はfloat  
  を使用する。

    他にも
    flexboxは記述もシンプルでレスポンシブ対応も簡単。
    わざわざfloatを解除しなくても、縦並びにすることができる。

    flexは子要素の幅の合計値が親の幅を超えている場合、tableのように自動計算され子要素の幅が調整され、2段になるなど、崩れない。  
    一方floatは子要素の幅の合計値が親の幅を超えている場合、子要素の幅は変わらず、2段になり崩れてしまう。

    flexは横並びの要素を高いほうに合わせて同じ高さにできるが、floatは同じ高さにはならない。

 <br>


  * 疑似要素のbeforeとafter  

    HTMLには書かれていない要素もどきをCSSで作ることができる。  
    文字や記号はもちろん、画像を挿し込んだり、空白にして見えない要素として使用することもできる。  
    使用用途としては吹き出し、アイコン、見出しの英字の配置などに使われる。

    beforeは指定した要素内にあるコンテンツの直前に、afterは指定した要素内にあるコンテンツの直後に配置される。  
    imgタグやbrタグ、inputタグなど要素内にコンテンツが存在しないタグにはbeforeとafterは配置することができない。

   * 例  
  ```HTML
    <p class="example">これは例文です</p>
  ```

  ```css
    example::before {
    content: '「';
    〜スタイル指定〜
    }

    .example::after {
    content: '」';
    〜スタイル指定〜
    }
    /*  表示は  「これは例文です」  となる
  ```

  <br>

* flex boxの種類  

  ・display: block;	インライン要素をブロック要素に変換し、縦に並べることができる。  
  ・display: inline;	指定された要素はインライン要素として表示されます  
  ・display: inline-block;	指定された要素はインライン要素とブロックレベル要素の特性を併せ持ちます  
  ・display: flex;	指定された要素の子要素は横並びになる  
  ・display: none;	指定された要素は非表示になる  

  <br>
  
  * display: flex;と合わせて使用するプロパティ

    * justify-content: 〇〇;  
    子要素は横並びの状態で
    子要素の横並びの間隔が以下で指定した配置になる。  

      ・justify-content: flex-start; 左寄せ  
      ・justify-content: flex-end; 右寄せ  
      ・justify-content: center; 子要素同士の余白なく中央    
      ・justify-content: space-between; 両端が左右に寄り、等間隔の余白ができる。  
      ・justify-content: space-around; 両端が左右に寄り、両端の余白と要素間の余白が1:2  

    <br>

    * align-items: 〇〇;  
    子要素は横並びの状態のまま縦軸方向（垂直方向）で以下で指定した配置になる。  

      ・align-items: flex-start; 上辺を合わせて上揃え  
      ・align-items: flex-end; 下辺を合わせて下揃え  
      ・align-items: center; 子要素の中心を合わせて中央揃え    
      ・align-items: baseline; flexbox  子要素のベースライン(テキストを記述した際のテキストの下部)
      に合わせて配置。  
      テキストの大きさによっても位置が変わる。  
      ・align-items: stretch; 親要素のサイズに合わせて、指定した全ての子要素が伸縮する。

    <br>

    * flex-direction: 〇〇;  
    子要素の並び順、方向（縦横）が以下で指定した配置、並び順になる。  

      ・flex-direction: row; 左から右に並べる（初期値） 
      ・flex-direction: row-reverse; 右から左に並べる  
      ・flex-direction: colum; 上から下に並べる（軸を横から縦に変更）    
      ・flex-direction: colum-reverse; 下から上に並べる（軸を横から縦に、また並び順も変更）


  * text-alignとvertical-alignとの違い
    justify-contentとtext-alignは同じ横方向（水平方向）に、  
    align-itemsとvertical-alignは同じ縦方向（垂直方向）の指定した位置に配置するプロパティだが、text-alignとvertical-alignはインライン要素とインラインブロック要素にしか作用しないと言う違いがある。

  * 例  
    ```HTML
      <h2 class="heading-name">新着情報</h2>
    ```

    ```CSS
    .heading-name {
      text-align: center;
    }
    /* justify-contentとは違いその配置したい要素自体に記述し、一行の記述だけで配置することができるが
    hタグなどのインライン要素とインラインブロック要素にしか作用しない。
    また、floatやpositionなどの浮いている要素にも作用しない。
    ```


 <br>

* positionプロパティ  

  * position: 〇〇;  
    子要素の並び順、方向（縦横）が以下で指定した配置、並び順になる。  

      ・position: absolute;  親要素を基準とした配置  
      子要素にこれを記述した際、親要素にposition: relative;を記述すると親要素の左上の角を基準とするが、親要素にposition: relative;が記述されていない場合は、ブラウザの左上の角が基準となる。  

      ・position: relative; 本来の表示位置を基準に配置

      ・position: fixed; 特定の位置に固定して表示  
        これを使用するとスクロールしても位置が変わらない。    
      
      


    <br>

* form要素  
    フォーム関連要素の集まりを表すブロック要素。
    このなかに、入力フォームや送信フォームを作成する。  
<br>
  * form要素の中に記述できる要素  
<br>

    ・input要素  
      フォームの入力欄や実行ボタンなどを作成することができるインライン要素。  
      input要素にはtype属性という設定があり、それを指定することによって様々な種類のフォーム部品を作り出すことができる。 


    | type属性     | 用途                                       |
    | ----------  |------------------------------------------- |
    | text        | １行のテキスト入力欄を作成                     |
    | checkbox    | チェックボックスを複数作成                     |
    | radio       | 複数の中から１つしか選択できないラジオボタンを作成 |
    | submit      | 送信ボタンを作成                             |

  <br>

    * 例  
    ```HTML  
      <input type="text"   placeholder="NAME"   class="name-form">
     <!-- この記述で１行のテキスト入力欄ができ、「NAME」と言う仮の文字が入った状態で表示される。 -->
    ```

 
  ・text area要素  
    複数行のテキスト入力欄を作成するインライン要素  


  ・value属性  
   フォームの送信をした時に、どのような値を送信するのかを決めることができる。送信ボタンに限っては、value属性で指定した文字が、送信ボタンに表示される。

   * 例  
    ```HTML
      <input type="submit" value="SEND" class="send">
      <!-- この記述で送信ボタンでき、「SEND」と言う仮の文字が入った状態で表示される。 -->
    ```
  
*  メモ

< title >タグ  
ページのタイトルを記述するタグ。
Webページのコンテンツにどんな内容が書かれているか、簡潔に示す文言をマークアップするためのHTMLタグとなります。ユーザーの検索意図を考慮する必要があります。

  < meta >タグ  
ページについての説明文を記述。検索エンジンでページタイトルとともに表示される部分。
ユーザーが検索した時に、どんなページなのか、求めている情報があるかを瞬時に判断できるよう、必要なキーワードを含めて記述するとよい。
文章前半にターゲットキーワードを含め、検索クエリとの関連性を強調する。
（ただし、キーワードを盛り込みすぎないように注意）
スマホやPCで表示できる文字数を意識した適切な長さの文章にする。




