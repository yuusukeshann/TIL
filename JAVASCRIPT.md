# **JAVASCRIPTメモ**

### メソッド ###

* addEventLitener()メソッド

  * 用途  
 イベント発火の際に実行する関数を定義するメソッド

  * 書き方  
 `要素.addEventListiner('イベント名', 関数)`


  * 例  
  window.addEventListener('load', function(){  
  })

    (ページが全て読み込まれた後に関数を実行する。)




* setAttributeメソッド

  * 用途  
  指定した要素上に新しい属性を追加、または既存の属性の値を変更する。

  * 書き方  
 `要素.setAttribute(name, value)`  
   nameは属性の名前を文字列で指定。  
   valueは属性に設定したい値を指定。

  * 例  
  ```javascript  
  const sample = document.getElementById("test")

  sample.setAttribute("style", "color: red;")  

  // <div id="test" style="color: red;">テスト</div> が取得できる
  ```


* removeAttributeメソッド

  * 書き方  
 	`要素.removeAttribute(name)`  
  nameは属性の名前を文字列で指定。

  * 用途  
 指定した要素から、特定の属性を削除する。

  * 例  
  ```javascript
  const apple = document.getElementById("apple")

  apple.removeAttribute("class")
  // <div id="apple">りんご</div> が取得できる
  ```


* thisメソッド

  * 用途  
 イベント発火元となった要素を取得できる。  
 使用する場面によって取得できるものが異なる。


  * 書き方  


  * 例  
  ```javascript
  pullDownButton.addEventListener('mouseover', function(){

  pullDownButton.setAttribute("style", "background-color:#FFBEDA;")
  })

  // これをthisで書き換えると
   pullDownButton.addEventListener('mouseover', function(){
    this.setAttribute("style", "background-color:#FFBEDA;")
  })

  // このように発火元となった要素を取得することができる。
  ```




* getAttributeメソッド

  * 用途   
 要素上の指定した属性の値を戻り値として返す。

  * 書き方  
  `要素.getAttribute('属性名')`
  

  * 例  
  ```javascript
  (HTML)
  <div class="contents" id="apple">りんご</div>
  
  (JAVASCRIPT)
  const apple = document.getElementById("apple")

  apple.getAttribute("class")
  // => contents というclass名が取得できる。
  ```

* innerHTMLプロパティ

  * 用途  
  HTML要素の取得や書き換えを行うことができる。
  

  * 例・書き方    
  ```javascript
  (HTML)
  <div class="contents" id="apple">りんご</div>
  
  (JAVASCRIPT)
  const apple = document.getElementById("apple")

  console.log(apple.innerHTML)
  // => りんご

  apple.innerHTML = "青リンゴ"
  console.log(apple.innerHTML)
  // => 青リンゴ
  
  ```

* document.getElementByIdメソッド

  * 用途  
 引数に渡したidを持つ要素を取得する。

  * 書き方  
  document.getElementById("id名")
  

  * 例  
  ```javascript
  //id名がhogeの要素を指定する場合
  document.getElementById("hoge")
  ```


* document.getElementsByClassNameメソッド

  * 用途  
  引数に渡したclassを持つ要素を全て取得する。
  

  * 例・書き方
  ```javascript
   //class名がfugaの要素を指定する場合

  document.getElementsByClassName("fuga")
  ```




  * document.querySelectorAllメソッド

  * 用途  
  HTML上から引数で指定したセレクタに合致するものと全て取得する。
 
  
  * 例・書き方   
  ```javascript
  //class名がfugaの要素を指定する場合
  document.querySelectorAll(".fuga")

  //id名がhogeの要素を指定する場合
  document.querySelectorAll("#hoge")
  
  //h1タグの要素を指定する場合
  document.querySelectorAll("h1")

  //セレクタ名を指定した要素のうち、一番最初に見つかった要素だけ取得
  document.querySelector("セレクタ名")
  
  ```

  * メモ  getElementsByClassNameとquerySelectorAllの違い  
  
    どちらも指定したクラスを取得できるメソッドだが、この2つの違いは戻り値にあり、前者はHTMLCollectionというオブジェクトを、後者はNodeListというオブジェクトを戻り値として返す。
  
    このHTMLCollectionとNodeListでは使えるメソッドが違う。
    例えばforEach関数を使用する場合は、NodeListオブジェクトを戻り値として返すquerySelectorAllを使用する。



* メソッド

  * 用途 


  * 書き方  
  
  

  * 例  
  ```javascript
  

  ```


  