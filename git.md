# WindowsへのGitとSourceTreeのインストール

## 1. Gitをインストール
* Gitで検索し、[オフィシャルサイト](http://git-csm.com/)にアクセス
* Windows版をダウンロード
* ダブルクリックしてインストール  
「Adjusting your PATH environment」で「Use Git from the Windows Command Prompt」を選択  
「Configuring the line ending conversions」で「Checkout as-is, commit as-is」を選択

## Gitの参考書
* [Pro Git日本語版](http://git-scm.com/book/ja/)
* [Pro Git日本語版電子書籍公開サイト](https://progit-ja.github.io/)

## 2. Gitの設定
* 「コマンド プロンプト」を起動
* 名前とe-mailアドレスを設定する  
e-mailアドレスは、GitHubなどで使用するつもりのものを指定するとよい  
```
git config --global user.name "自分の名前"
git config --global user.email "自分のe-mail"
```
* 設定を確認する
```
git config --list
```

## 3. GitHubのアカウントを作成
* GitHubで検索し、[オフィシャルサイト](https://github.com/)にアクセス
* トップページでユーザー名、メール・アドレス、パスワードを指定して、サインアップする
* 「Choose your personal plan」で、「Free」が「Chosen」であることを確認し、「Finish sign up」をクリック
* メールが"\[GitHub\] Please verify your email ..."といった件名で届くので、メール中のリンクをクリック
* 表示されたサイトで「Confirm」をクリック

## 4. SourceTreeをインストール
* SourceTreeで検索し、[オフィシャルサイト](http://www.atlassian.com/ja/software/sourcetree)にアクセス
* Windows版をダウンロード
* ダブルクリックしてインストール
* SourceTreeを起動する  
もしも「グローバル無視設定ファイルを作成しますか？」と聞かれたら「No」を選択  
「アカウントを追加」で「アカウント」を「GitHub」とし、GitHubの「ユーザー名」と「パスワード」を入力  
「初めてのリポジトリをクローン...」を「スキップ」   
「SSHキーを読み込みますか？ 'いいえ'をクリックしても、後でいつでも追加できます。」で「No」を選択

## 5. SourceTree付属のPuTTYでSSH Keyを作成
* SourceTreeを起動しておく
* 「ツール」→「SSHキーの作成/インポート」
* 「Actions」の「Generate a public/private key pair」の「Generate」をクリック。
* 「Key」に"Please generate some randomness by moving the mouse over the blank area.(空の領域の中でマウスを動かしてランダムなものを生成してください)"と表示されるので、ゲージがいっぱいになるまでランダムにマウスを動かす。

* パスフレーズを指定するか、しないかを選ぶ。  
公開鍵暗号の秘密鍵を、自分のパソコンに保存する必要があるが、秘密鍵を暗号化して保存する場合はパスフレーズを指定、暗号化しない場合はパスフレーズを指定しない。  
暗号化した方が安全だが、その場合、SourceTreeを起動するときにパスフレーズの入力を求められる。暗号化しないと安全性が下がるが、SourceTreeを起動するときにパスフレーズの入力は求められない。

* パスフレーズを指定する場合は、「Key」の「Key passphrase」と「Confirm passphrase」にパスフレーズを入力する。

* 公開鍵暗号の秘密鍵を保存する。  
「Actions」の「Save the generated key」で「Save private key」をクリック。  
パスフレーズを指定しないと「Are you sure you want to save this key without a passphrase to protect it?」と表示される。  
適当なフォルダにid_rsa.ppkなどといった名前で保存する。仮に暗号化してあっても他人にファイルが流出しないように注意する。特にパスフレーズを指定しないで暗号化しなかった場合は流出したらアウト。

* SourceTreeの「ツール」→「オプション」  
「全般」タブの「SSHクライアントの設定」の「SSHキー」に、作成した公開鍵暗号の秘密鍵のファイルを指定する。

## 6. GitHubにSSH Keyを登録
* SourceTreeを起動しておく
* 「ツール」→「SSHキーの作成/インポート」
* 「Load an existing private key file」で「Load」をクリックし、秘密鍵のファイルを指定する
* 「Key」の「Public key for pasting into OpenSSH authorized_keys file」の内容をコピーする

* GitHubのWebサイトで、右上の方にある「Account Settings」(工具のアイコン)をクリック
* 「SSH keys」を選択
* 「Add SSH Key」で「Title」は適当に、「Key」にSourceTreeからコピーした内容をペーストし、「Add key」をクリック
