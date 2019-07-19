# pythonを使ってゲームを作ろう！！


## 今日作るゲーム：石取りゲーム

### ルール


１５個の石を順番に取っていきます。取ることのできる石の数は、「１個」か「２個」しか選べません。

最後の一個を取ったら、負けです。**最後の一個を取らないようにする**ゲームです。


<input id="startBtn" type="button" value="スタート"  style="display:block;" onClick="gameStart()"/>
<div id="stoneGame" style="display:none;">
<p id="stones">〇〇〇〇〇〇〇〇〇〇〇〇〇〇〇</p>

<input id="oneBtn" type="button" value="１個" onClick="getOne()" />
<input id="twoBtn" type="button" value="２個" onClick="getTwo()" />

<p id="stoneMsg"></p>
<p id="stoneMsgCp"></p>

</div>

<p id="gameResult"></p>

<script>
var stoneNum = 15;

function gameStart(){
    var stoneGame = document.getElementById("stoneGame");
    var startBtn = document.getElementById("startBtn");
    stoneGame.style.display = "block";
    startBtn.style.display = "none";
    stoneNum = 15;
    var gameResult = document.getElementById("gameResult");
    gameResult.innerText = "";
    setStone(15, false);
}

function gameEnd(isLose){
    var stoneGame = document.getElementById("stoneGame");
    var startBtn = document.getElementById("startBtn");
    stoneGame.style.display = "none";
    startBtn.style.display = "block";
    startBtn.value = "もう一度";
    var gameResult = document.getElementById("gameResult");
    if(isLose){
        gameResult.innerText = "あなたの負け";
    }else{
        gameResult.innerText = "あなたの勝ち";        
    }
}

function setStone(num, isUser){
    var stone ="";
    for(var i=0; i < num;i++){
        stone = stone + "〇";
    }
    if(num <= 0){
        gameEnd(isUser);
    }
    var stones = document.getElementById("stones");
    stones.innerText = stone;
}

function getOne(){
    getUser(1);
    changeBtn(true);
    if(stone <= 0)
        return;
    setTimeout("getCp(2)", 1000);
}

function getTwo(){
    getUser(2);
    changeBtn(true);
    if(stone <= 0)
        return;
    setTimeout("getCp(1)", 1000);
}

function getUser(userNum){
    stoneNum = stoneNum - userNum;
    setStone(stoneNum, true);
    var msgcp = document.getElementById("stoneMsgCp");
    msgcp.innerText ="";
    var msg = document.getElementById("stoneMsg");
    msg.innerText = "あなたは" + userNum + "個取りました。";
}

function getCp(cpNum){

    if(stoneNum == 3){
        cpNum = 2;
    }else if(stoneNum == 2){
        cpNum = 1;
    }
    
    var msgcp = document.getElementById("stoneMsgCp");
    stoneNum = stoneNum - cpNum;
    setStone(stoneNum, false);
    msgcp.innerText = "コンピュータは" + cpNum + "個とりました。";
    changeBtn(false);    
}

function changeBtn(doDisable){
    var oneBtn = document.getElementById("oneBtn");
    var twoBtn = document.getElementById("twoBtn");
    oneBtn.disabled = doDisable;
    twoBtn.disabled = doDisable;
}

</script>


<hr/>
<br/>
<br/>


# Lesson0 はじめに
## プログラミングとは？

<img src="img/typing.jpg"/>



**プログラム** = 「**命令**」

<br/>
<br/>

 
 
命令：「右へ１０歩動く」

<br/>


<img src="img/scratch.png"/>

<br/>
<br/>
 
 
命令：「左へ１０歩動く」

<br/>


<img style="transform: scale(-1, 1);" src="img/scratch.png"/>


<br/>
<br/>
<br/>



プログラミングとは...

**コンピュータへ命令を作ること**です!!


<img src="img/program.jpg"/>


<hr/>
<br/>
<br/>
<br/>


## pythonとは？

<img src="img/python.jpg"/>



pythonは、プログラムを作ることができるプログラミング言語(コンピュータが理解できる言語)の一種です。



- python言語は、

「**誰が書いても綺麗なプログラムになるように作られた言語**」


- シンプル
- 見やすい



## なぜpythonが注目されているか？


- 人気急上昇

<img src="img/lang-programing.png" />

- 豊富なライブラリ

<img src="img/ai.jpg" />


<hr/>
<br/>
<br/>



## 環境構築


python講座で使用するツールをインストールしましょう！
使うものは、以下のものです。


- python　（バージョン３のもの）
- pythonを動かすアプリケーション

<br/>
<br/>


## python バージョン3

pythonは多くのOSでは、すでにインストールされている場合が多いですが、多くの場合は、python 2.X.Xのバージョンであることが多いです。

python2.X.Xのバージョンとpython3.X.Xのバージョンは、異なる部分がとても多いです。

本講義では、python3.X.X を使用するので、下記のURLからダウンロードして、インストールまで行いましょう。



[https¥://www.python.org/downloads/](https://www.python.org/downloads/)


<br/>
<br/>


## pythonを動かすアプリケーション

続いて、pythonを動かすアプリケーションをインストールします。


基本的には、文字が書けるアプリケーション（Visual studio code, さくらエディタなど）なら、大丈夫です。


もし、今日をきっかけに勉強してみたいという人へのオススメは、PyCharmです。



PyCharmをインストールする方は、こちらからどうぞ


[https¥://www.jetbrains.com/pycharm/](https://www.jetbrains.com/pycharm/
)




環境構築が終わったら、いよいよプログラムを書いていきましょう！！！


※テキストエディタによっては、コマンドラインの機能がないものもありますので、Terminal(Mac),コマンドプロンプト(windows)が必要な場合もございます。


<hr/>
<br/>
<br/>
<br/>


# Lesson1 出力しよう！


## Hello World

まずは、最初のプログラムの定番、「Hello World!!」と出力してみます。


### まずは、ファイルを作ってみましょう！


pythonのファイルは、


```python
xxxxx.py
```


というファイル名で作ることができます。


ファイル名に「.py」が付いていれば、全部pythonのプログラムです。


今回は、


```python
lesson1.py
```

という名前で作成しましょう。

<br/>
<br/>


## Hello Wolrd!!のプログラムを作ろう

それでは、作成したファイルに、以下のプログラムを書いていきましょう。


```python
print("Hello world!!")
```

<br/>
<br/>

### 作ったプログラムを実行しよう！


ファイルを実行する時は、以下のように入力して、実行します。


```python
python xxxxx(ファイル名).py
```

今回の場合は、

```python
python lesson1.py
```

と入力します。

<br/>
<br/>


## print文の様々な書き方

「" "」の他にも「' '」を使っても良い。

いずれかに囲まれた物を表示します。


```python
print('Hello world!!')
```


<br/>
<br/>

<div class="enshu">
    <p class="enshu-title">演習：</p>
    <p class="enshu-q">
        好きな文字を出力してみよう！！
    </p>
</div>


<br/>
<br/>


<div class="enshu">
    <p class="enshu-title-next">演習(早く終わった人)：</p>
    <p class="enshu-q">
        ①「Let's enjoy programing!!」と出力してみましょう。
    </p>
    <br/>
    <p class="enshu-q">
        ②「I am "HERO".」と出力してみましょう。
    </p>
</div>


<hr/>
<br/>
<br/>


# Lesson2 変数


lesson2.pyのファイルを作りましょう！


## 変数

変数とは、値が変化する数のことです。


例えば、以下のプログラムは、aという変数に10を入れるという意味です。


```python
a = 10
```

<br/>
<br/>

#### 本当に入っているか確認してみよう！！


新しいファイルlesson2.pyにコピーして、以下のプログラムを実行させてみよう。


```python
a = 10

print(a)
```

### ◼変数の特徴その①：変数は値が変化する

ファイルlesson2.pyにコピーして、以下のプログラムを実行させてみよう。

```python
a = 10
a = 20

print(a)
```

※上書きされます。

<br/>
<br/>


### ◼変数の特徴その②：変数はいくつも作れる！文字も入れることができる!

ファイルlesson2.pyにコピーして、以下のプログラムを実行させてみよう。


```python
a = 10
b = 20
c = "hello"

print(a)
print(b)
print(c)
```

<br/>
<br/>


次のプログラムを動かして見て出力結果を見てみましょう。

```python

a = 10
b = 20
c = "hello"

a = b

print(a)
print(b)
print(c)

```



<br/>
<br/>

**「a = b」は、aにbの値を入れるという意味になります。**

<br/>
<br/>


つまり、「**右のものを左に入れる**」という意味になります。


<br/>
<br/>


<div class="enshu">
    <p class="enshu-title">演習：</p>
    <p class="enshu-q">
    次のプログラムの出力結果が何になるか答えなさい
    <pre style="background-color: #364549;color:#ffffff;margin: 5px;">
    a = 10
    b = 20

    c = a
    a = b
    b = c

    print(a)
    </pre>

   </p>
   <input type="text" size="10" />
</div>


<div class="enshu">
    <p class="enshu-title">演習：</p>
    <p class="enshu-q">
    次のプログラムの出力結果が何になるか答えなさい
    <pre style="background-color: #364549;color:#ffffff;margin: 5px;">

    a = 'おはよう'
    b = 'こんにちは'
    c = 'こんばんは'

    d = a
    a = b
    b = c
    c = d

    print(c)

    </pre>

   </p>
　 
   <input type="text" size="10" />
</div>




<hr/>
<br/>
<br/>


# Lesson3 型

lesson3.pyを作ろう！

## 型

プログラムは、数字と文字を別々に識別しています。


下のプログラムは、numには「１０」が入っています。


```python
num = "10"
```

この「10」は、文字でしょうか？数字でしょうか？


答えは、以下のプログラムを動かしてみましょう。

### lesson3.pyにコピーして実行してみよう！


```python
num = "10"

print(num)
print(type(num))
```


以下のように表示されます。


```python
10
<class 'str'>
```

<br/>
<br/>

**<class 'str'>**と表示れたら、「**文字**」であるという意味になります。


<br/>
<br/>


### lesson3.pyを以下のように書き換えて、もう一度実行してみましょう。


```python
num = 10

print(num)
print(type(num))
```

今度は、以下のように表示れました。


```python
10
<class 'int'>
```

<br/>
<br/>

**<class 'int'>**と表示れたら、「**数字**」であるという意味になります。

<br/>
<br/>


## 覚えること

|型| |
| str | 文字 |
| int | 数字 |


<br/>
<br/>


演習：次の変数aとbの型を調べてみよう

lesson3.pyにコピーして、プログラムを書きましょう。


```python
a = "100"
b = 100
```

<hr/>
<br/>
<br/>


#Lesson4 演算

lesson4.pyを作りましょう。

## 演算

演算とは、+,-,×,÷をすることです。

<br/>
<br/>


例えば、プログラムで書くと以下のように書くことができます。

lesson4.pyにコピーして実行してみよう。

```python
a = 10
b = 7
print(a + b)
```
<br/>
<br/>

### その他の計算



```python
a = 10
b = 7

print(a + b) #足し算
print(a - b) #引き算
print(a * b) #かけ算
print(a / b) #割り算
print(a % b) #剰余（割り算の余り）
print(a ^ b) #べき乗
```

<br/>
<br/>
<br/>


## 演習：全部の記号をキーボードで押せるかな？


足し算の記号：<input type="text" size="3" />

引き算の記号：<input type="text" size="3" />

かけ算の記号：<input type="text" size="3" />

割り算の記号：<input type="text" size="3" />

剰余の記号：<input type="text" size="3" />

べき乗の記号：<input type="text" size="3" />



<br/>
<br/>
<br/>


### 文字の足し算もできます。

lesson4.pyの一番下の行に追加してみよう。

```python
print("おはよう" + "ございます。")
```

<br/>
<br/>
<br/>


演習：

```python
a = 10
b = 7

c = a + 1
d = b -1

print(c)
print(d)
```

それぞれどんな結果になるでしょうか？

print(c):<input type="text" size="3" />

print(d):<input type="text" size="3" />

<br/>
<br/>
<br/>


```python
a = 10

a = a + 1

print(a)
```

どんな結果になるでしょうか？

<input type="text" size="3" />


<br/>
<br/>
<br/>


```python
b = 7

b = b - 1

print(a)
```

どんな結果になるでしょうか？

<input type="text" size="3" />


<br/>
<br/>
<br/>



```python
print(2 + 3 * 5)
```

どんな結果になるでしょうか？

<input type="text" size="3" />


<hr/>
<br/>
<br/>

# Lesson5 入力しよう！

lesson5.pyを作りましょう！

<br/>
<br/>

## 入力

printで値を出力しましたが、入力する方法を学びます。

入力の書き方は、


```python
変数名 = input("メッセージ")
```

<br/>
<br/>

試しに、lesson5.pyに以下のプログラムを書いて、実行してみましょう。


```python
s = input("何か入力してください。：")

print("入力された値を表示します。")
print(s)
```

<br/>
<br/>

演習：


<hr/>
<br/>
<br/>


# Lesson5 if文


### if文
ここからは、条件分岐について学んでいきます。


例えば、テストの点数が、100点の時は、「満点」と表示したい時は？


```python
test = 100


if test == 100:
    print('満点')
```


このように、　== は左と右が同じという意味になります。


これを比較演算子と呼びます。


その他の比較演算子は以下のようなものがあります。








### else文
続いて、テストの点数が、70点以上は「合格」。70点未満は「不合格」と表示したい時は？


```python
test = 70


if test >= 70:
    print('合格')
else:
    print('不合格')
```




### elif文
最後に、80点以上は「A」、60点以上は、「B」、それ以外は、「C」と表示したい時は？


```python
test = 60


if test >= 80:
    print('A')
elif test >= 60:
    print('B')
else:
    print('C')
```






演習：



<hr/>
<br/>
<br/>



# Lesson6 for文
### for文の書き方１


例えば、"●"を5個表示したい時は？


```python
print('●')
print('●')
print('●')
print('●')
print('●')
```


って書くの大変ですよね...。（ちょっとカッコ悪い）


そこで、for文の出番です。


同じ処理をする場合は、何回その処理をやるのか書くだけで、繰り返し処理をしてくれます。


```python
for i in range(i):
    print('●')
```






演習：



<hr/>
<br/>
<br/>


# Lesson7 関数
### 


例えば、下記の処理を何回かやりたい時があります。


```python
a = a + b
print('a')
```


その時に、


```python
a = a + b
print('a')


a = a + b
print('a')


a = a + b
print('a')


a = a + b
print('a')
```


と書くのは少し不便です。


そんな時に、役立つのが、関数です。


関数は、処理を一つにまとめてくれるとても便利なものです。




```python


def a(
        
):
    print('関数が呼ばれました')


a()
a()
a()
```






演習：



<hr/>
<br/>
<br/>


# Lesson8 ゲームを作ってみよう！
### 




<script>
function getCorrect(id){
    changeText(id,'正解を表示',"#de4e2e");
}
function moreQuestion(id){
    changeText(id,'挑戦!',"#228822");
}
function getNone(id){
    changeText(id,'表示',"#334433");
}
function getHint(id){
    changeText(id,'ヒント',"#334433");
}
function getReference(id){
    changeText(id,'参考','#228822');
}
function readDigression(id){
    changeText(id,'余談','#228822');
}
function changeText(id,text,color){
    let span = document.getElementById('span_'+id);
    let btn = document.getElementById('btn_'+id);
    if(btn.value == '非表示'){
        btn.value = text;
        span.style.display = 'none';
    }else{
        btn.value = '非表示';
        span.style.display = 'block';
        span.style.color = color
    }

}

function picturesClickEvent(id){
    let nextId = id == 8 ? 1 : (id+1);
    let prev = document.getElementById('pictures_'+id);
    let next = document.getElementById('pictures_'+nextId);
    prev.style.display = 'none';
    next.style.display = 'block';
}


var enshu = document.getElementsByClassName('enshu');
var enshuTitle = document.getElementsByClassName('enshu-title');
var enshuTitleNext = document.getElementsByClassName('enshu-title-next');
var enshuQ = document.getElementsByClassName('enshu-q');

for (var i = 0; i < enshu.length; i++) {
  enshu[i].style.backgroundColor = "#FFFFFF";
  enshu[i].style.border = "thin solid black"
}
for (var i = 0; i < enshuTitle.length; i++) {
  enshuTitle[i].style.fontSize = "25px";
  enshuTitle[i].style.padding = "5px";
  enshuTitle[i].style.backgroundColor = "blue";
  enshuTitle[i].style.color = "white";
    
}
for (var i = 0; i < enshuTitleNext.length; i++) {
  enshuTitleNext[i].style.fontSize = "25px";
  enshuTitleNext[i].style.padding = "5px";
  enshuTitleNext[i].style.backgroundColor = "green";
  enshuTitleNext[i].style.color = "white";
    
}
for (var i = 0; i < enshuQ.length; i++) {
  enshuQ[i].style.fontSize = "12px";
  enshuQ[i].style.color = "green";
  enshuQ[i].style.padding = "5px";
}


</script>
