# Git_kadai
## 実験の手順（2人用）
### 事前準備1：実験用フォルダについて
　事前準備としてhttps://drive.google.com/drive/u/0/folders/1DEkfqzE7f9zRV7bKkmUiXQs5Gmr8kK1P のzipフォルダ<br>
　をダウンロードおよび解凍しておくこと．<br>
　各フォルダの詳細は以下の通りである．<br>
　・AGDRec_132F.zip（画面録画用ソフト）<br>
　・Git_bash.zip（ターミナル用ソフト）<br>
　・kadai.zip（課題用フォルダ）<br>
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
### 3.初期実装
　初期実装として解凍したkadai.zipの中身を作業ディレクトリ直下に移動しリモートリポジトリと同期させる．<br>

### 4.課題
#### 4-1.課題1 GameMain.javaで文章の表示
　[変更するファイル]　GameMain.java<br>
　以下の実行例の通りに文章を表示する．<br>
　[実行例]
```
$ java GameMain
 1:グー 2:チョキ 3:パー
 じゃんけん...
```

#### 4-2.課題2 Playerの手の決定とその表示
　[変更するファイル]　GameMain.java, Player.java, Hand.java<br>
　Playerは1,2,3のいずれかの数値を入力する．<br>
　1,2,3以外の入力があった場合は実行例の通りにエラー文を表示し，再入力させる．<br>
　1,2,3のいずれかの入力がされた場合は，それぞれ対応した手を表示する．<br>
　対応は1ならば"グー",2ならば"チョキ",3ならば"パー"<br>
　<br>
　[decidesPlayerHandメソッド]<br>
　PlayerクラスではdecidesPlayerHandメソッドを定義する<br>
　引数なし．戻り値はint型．Playerの入力した数値(1,2,3のいずれか)を返す．<br>
　Playerからの数値の入力に対するエラー文や再入力などの処理を行う．<br>
　<br>
　[getHandNameメソッド]<br>
　HandクラスではgetHandNameメソッドを定義する<br>
　引数はint型．PlayerクラスのdecidesPlayerHandメソッドの戻り値が代入される．<br>
　戻り値はString型．Playerの入力した数値を対応する手に変更し，その値を返す．<br>
　<br>
　[GameMain.java]<br>
　PlayerクラスのdecidesPlayerHandメソッド，HandクラスのgetHandNameメソッドを使って<br>
　実行例のようにPlayerの手を表示する処理を追加する．<br>
　[実行例]
```
$ java GameMain
　1:グー 2:チョキ 3:パー
　じゃんけん...
->1
　プレイヤー : グー

$ java GameMain
　1:グー 2:チョキ 3:パー
　じゃんけん...
->4
　1~3の数値を入力して下さい。
->2
　プレイヤー : チョキ
 
$ java GameMain
　1:グー 2:チョキ 3:パー
　じゃんけん...
->three
　1~3の数値を入力して下さい。
->3
　プレイヤー : パー
```

#### 4-3.課題3 Computerの手の決定とその表示
　[変更するファイル]　GameMain.java, Computer.java<br>
　[decidesComputerHandメソッド]<br>
　ComputerクラスではdecidesComputerHandメソッドを定義する<br>
　引数なし．戻り値はint型．1,2,3のいずれかの数値を返す．<br>
　Randomメソッドを使い，1,2,3の数値をランダムに返す機能を実装する．<br>
　<br>
　[GameMain.java]<br>
　課題2と同様にComputerクラスのdecidesComputerHandメソッド，HandクラスのgetHandNameメソッドを使って<br>
　実行例のようにComputerの手を表示する処理を追加する．<br>
　[実行例]
```
$ java GameMain
　1:グー 2:チョキ 3:パー
　じゃんけん...
->1
　プレイヤー : グー
　コンピュータ : パー
```
#### 4-4.課題4 勝敗判定とその表示
　[変更するファイル]　GameMain.java, VictoryOrDefeat.java<br>
　[decidesComputerHandメソッド]<br>
　VictoryOrDefeatクラスではdecisionVictoryOrDefeatメソッドを定義する<br>
　引数はint型のcomputerHandとplayerHand．それぞれじゃんけんの手に対応する1,2,3のいずれかの数値が代入される．戻り値なし．<br>
　課題2,3でGameMain.javaに実装したPlayerおよびComputerの手を表示する処理はこのメソッド内で行うよう変更する．<br>
　computerHandとplayerHandの値を比較して勝敗判定を行い，それを表示する機能を実装する．<br>
　<br>
　[GameMain.java]<br>
　PlayerおよびComputerの手を表示はVictoryOrDefeatクラスに移動する．<br>
　VictoryOrDefeatクラスのdecisionVictoryOrDefeatメソッドを呼び出す．<br>
　[実行例]
```
$ java GameMain
　1:グー 2:チョキ 3:パー
　じゃんけん...
->1
　プレイヤー : グー
　コンピュータ : パー
　負け

$ java GameMain
　1:グー 2:チョキ 3:パー
　じゃんけん...
->2
　プレイヤー : チョキ
　コンピュータ : チョキ
　あいこ

$ java GameMain
　1:グー 2:チョキ 3:パー
　じゃんけん...
->3
　プレイヤー : パー
　コンピュータ : グー
　勝ち
```
