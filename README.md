# Git_kadai
## 実験の手順（2人用）
### 事前準備1：実験用フォルダについて
　事前準備としてhttps://drive.google.com/drive/u/0/folders/1DEkfqzE7f9zRV7bKkmUiXQs5Gmr8kK1P のzipフォルダ<br>
　をダウンロードおよび解凍しておくこと．<br>
　各フォルダの詳細は以下の通りである．<br>
　・AGDRec_132F.zip（画面録画用ソフト）<br>
　・Git_bash.zip（ターミナル用ソフト）<br>
　・kadai1.zip（課題用フォルダ1）<br>
　・kadai2.zip（課題用フォルダ2）<br>
### 事前準備2：個人アクセストークンの取得
　ターミナル上でGitHubの操作を行うために必要な個人アクセストークンの取得を行う．<br>
　GitHubのページの右上のプロフィール画像をクリックし，Settingsをクリックする．<br>
　サイドバーから[Developer settings]→[Personal access tokens]に移動し，[Generate new token] をクリックする．<br>
　[設定]<br>
　　Note：任意のトークン名<br>
　　Expiration：任意の有効期限<br>
　　Select scopes：[repo]にチェック<br>
　設定が完了したら，[Generate token]をクリックし，トークンを取得する．<br>
　※トークンの取得直後以降は再表示できないため，必ずメモしておくこと
### 1.リモートリポジトリの作成
　https://github.com/ にてGitHubにログインした後，新しくリポジトリを作成する．
### 2.Collaboratorの追加
　リポジトリのページから[Settings]→[Manage access]と移動し，共同開発者の追加を行う．<br>
　[Add people]をクリックし，ユーザー名を入力して共同開発者を追加する．

### 3.kadai1
　初期実装として解凍したkadai.zipの中身を作業ディレクトリ直下に移動しリモートリポジトリと同期させる．<br>
　※以下の[実行例]における <- のマークがついている⾏はユーザによる入力を表したものである。
#### 3-1.課題1 GameMain.javaで文章の表示
　[変更するファイル]　GameMain.java<br>
　以下の実行例の通りに文章を表示する．<br>
　[実行例]
```
$ java GameMain
1:グー 2:チョキ 3:パー
じゃんけん...
```

#### 3-2.課題2 Playerの手の決定とその表示
　[変更するファイル]　GameMain.java, Player.java, Hand.java<br>
　Playerは1,2,3のいずれかの数値を入力する．<br>
　1,2,3以外の入力があった場合は実行例の通りにエラー文を表示し，再入力させる．<br>
　1,2,3のいずれかの入力がされた場合は，それぞれ対応した手を表示する．<br>
　対応は1ならば"グー",2ならば"チョキ",3ならば"パー"<br>
　<br>
　[decidesPlayerHandメソッド]<br>
　 PlayerクラスではdecidesPlayerHandメソッドを定義する．<br>
　 引数なし．戻り値はint型．Playerの入力した数値(1,2,3のいずれか)を返す．<br>
　 Playerからの数値の入力に対するエラー文や再入力などの処理を行う．<br>
　[getHandNameメソッド]<br>
　 HandクラスではgetHandNameメソッドを定義する．<br>
　 引数はint型．PlayerクラスのdecidesPlayerHandメソッドの戻り値が代入される．<br>
　 戻り値はString型．Playerの入力した数値を対応する手に変更し，その値を返す．<br>
　[GameMain.java]<br>
　 PlayerクラスのdecidesPlayerHandメソッド，HandクラスのgetHandNameメソッドを使って<br>
　 実行例のようにPlayerの手を表示する処理を追加する．<br>
　[実行例]（<- のマークがついている⾏はユーザによる⼊⼒）
```
$ java GameMain
1:グー 2:チョキ 3:パー
じゃんけん...
1　<-
プレイヤー : グー

$ java GameMain
1:グー 2:チョキ 3:パー
じゃんけん...
4　<-
1~3の数値を入力して下さい。
2　<-
プレイヤー : チョキ
 
$ java GameMain
1:グー 2:チョキ 3:パー
じゃんけん...
three　<-
1~3の数値を入力して下さい。
3　<-
プレイヤー : パー
```

#### 3-3.課題3 Computerの手の決定とその表示
　[変更するファイル]　GameMain.java, Computer.java<br>
　[decidesComputerHandメソッド]<br>
　 ComputerクラスではdecidesComputerHandメソッドを定義する．<br>
　 引数なし．戻り値はint型．1,2,3のいずれかの数値を返す．<br>
　 Randomメソッドを使い，1,2,3の数値をランダムに返す機能を実装する．<br>
　[GameMain.java]<br>
　 課題2と同様にComputerクラスのdecidesComputerHandメソッド，HandクラスのgetHandNameメソッドを<br>
　 使って実行例のようにComputerの手を表示する処理を追加する．<br>
　[実行例]
```
$ java GameMain
1:グー 2:チョキ 3:パー
じゃんけん...
1　<-
プレイヤー : グー
コンピュータ : パー
```
#### 3-4.課題4 勝敗判定とその表示
　[変更するファイル]　GameMain.java, VictoryOrDefeat.java<br>
　[decidesComputerHandメソッド]<br>
　 VictoryOrDefeatクラスではdecisionVictoryOrDefeatメソッドを定義する<br>
　 引数はint型のcomputerHandとplayerHand．それぞれじゃんけんの手に対応する1,2,3のいずれかの<br>
　 数値が代入される．戻り値なし．<br>
　 課題2,3でGameMain.javaに実装したPlayerおよびComputerの手を表示する処理はこのメソッド内で<br>
　 行うよう変更する．<br>
　 computerHandとplayerHandの値を比較して勝敗判定を行い，それを表示する機能を実装する．<br>
　[GameMain.java]<br>
　 PlayerおよびComputerの手を表示はVictoryOrDefeatクラスに移動する．<br>
　 VictoryOrDefeatクラスのdecisionVictoryOrDefeatメソッドを呼び出す．<br>
　[実行例]
```
$ java GameMain
1:グー 2:チョキ 3:パー
じゃんけん...
1　<-
プレイヤー : グー
コンピュータ : パー
負け

$ java GameMain
1:グー 2:チョキ 3:パー
じゃんけん...
2　<-
プレイヤー : チョキ
コンピュータ : チョキ
あいこ

$ java GameMain
1:グー 2:チョキ 3:パー
じゃんけん...
3　<-
プレイヤー : パー
コンピュータ : グー
勝ち
```

### 4.kadai2
　初期実装として解凍したkadai2.zipの中身を作業ディレクトリ直下に移動しリモートリポジトリと同期させる．<br>
　※以下の[実行例]における <- のマークがついている⾏はユーザによる入力を表したものである。
#### 4-1.課題1 Main.javaで文章の表示
　[変更するファイル]　Main.java<br>
　以下の実行例の通りに文章を表示する．<br>
　[実行例]
```
$ java Main
私の名前はKateJonesです
年齢は20歳です
身長は1.735mです
体重は67.0kgです
BMIは22.257472448072814です
```

#### 4-2.課題2 名前,年齢をPeasonクラスで定義する
　[変更するファイル]　Main.java, Person.java<br>
　ここではMain.javaで定義されている名前と年齢をPerson.javaで定義するよう変更し，<br>
　Main.javaにPersonクラスのオブジェクト生成を追加する．<br>
　またそれに伴い，firstName,lastName,ageを引数としたコンストラクタをPerson.javaに実装する．<br>
　名前はfirstNameとlastNameの間に半角空白を入れたものに変更する．<br>
　<br>
　[実行例]
```
$ java Main
私の名前はKate Jonesです
年齢は20歳です
身長は1.735mです
体重は67.0kgです
BMIは22.257472448072814です
```

#### 4-3.課題3 Helthクラスの作成と各種メソッドの作成
　[変更するファイル]　Main.java, Person.java, Health.java<br>
　Main.javaで定義されている身長,体重,BMIをHealthクラスで定義および計算するようにに変更する．<br>
　それに伴い，Helth.javaでは身長と体重のデータの更新，BMIの計算，BMIが標準値であるかの判定の<br>
　3つのメソッドを作成する．<br>
　また，Person.javaではメンバ変数にHealthを追加し，身長・体重のデータの更新のメソッドを追加する．<br>
　最後に，Main.javaにprintDataメソッドを作成し，課題1で作成した名前,年齢,身長,体重,BMIの表示機能<br>
　およびBMIが標準値を満たしているかの表示機能を追加する．<br>
　BMIが標準値を満たしている場合は"標準値です"，満たしていない場合は"標準値の範囲外です"と表示する．<br>
　BMIの標準値の基準は「18.5以上25.0未満」とする．<br>
　<br>
　[実行例]
```
$ java Main
私の名前はKate Jonesです
年齢は27歳です
身長は1.735mです
体重は67.0kgです
BMIは22.257472448072814です
標準値です
```
#### 4-4.課題4 人物情報の入力機能の追加
　[変更するファイル]　Main.java<br>
　ファーストネーム,ラストネーム,年齢,身長,体重を入力する機能を追加する．<br>
　以下の実行例のように入力を促す文章の表示機能も追加すること．<br>
　<br>
　[実行例]
```
$ java Main
ファーストネームを入力してください。
Kate　<-
ラストネームを入力してください。
Jones　<-
年齢を入力してください。
27　<-
身長(m)を入力してください。
1.735　<-
体重(kg)を入力してください。
67.0　<-
私の名前はKate Jonesです
年齢は27歳です
身長は1.735mです
体重は67.0kgです
BMIは22.257472448072814です
標準値です

$ java Main
ファーストネームを入力してください。
Hello　<-
ラストネームを入力してください。
Kitty　<-
年齢を入力してください。
47　<-
身長(m)を入力してください。
0.45　<-
体重(kg)を入力してください。
0.9　<-
私の名前はHello Kittyです
年齢は47歳です
身長は0.45mです
体重は0.9kgです
BMIは4.444444444444445です
標準値の範囲外です
```
