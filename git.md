# WindowsへのGitとSourceTreeのインストール

## 1. Gitをインストール
* Gitで検索し、[オフィシャルサイト](http://git-csm.com/)にアクセス
* Windows版をダウンロード
* ダブルクリックしてインストール  
「Adjusting your PATH environment」で「Use Git from the Windows Command Prompt」を選択  
「Configuring the line ending conversions」で「Checkout as-is, commit as-is」を選択

## 2. SourceTreeをインストール
* SourceTreeで検索し、[オフィシャルサイト](http://www.atlassian.com/ja/software/sourcetree)にアクセス
* Windows版をダウンロード
* ダブルクリックしてインストール  
「Mercurialが見つかりませんでした」で「Mercurialを使いたくない」を選択  
「SSHクライアントの設定」で「PuTTY/Plinkを使う」を選択  
「SSHキーを読み込みますか？」で「No」を選択

## 3. SourceTree付属のPuTTYでSSH Keyを作成
* SourceTreeを起動しておく
* 「ツール」→「SSHキーの作成/インポート」
* 「Actions」の「Generate a public/private key pair」の「Generate」をクリック。
* 「Key」に"Please generate some randomness by moving the mouse over the blank area.(空の領域の中でマウスを動かしてランダムなものを生成してください)"と表示されるので、ゲージがいっぱいになるまでランダムにマウスを動かす。

* パスフレーズを指定するか、しないかを選ぶ。  
公開鍵暗号の秘密鍵を、自分のパソコンに保存する必要があるが、秘密鍵を暗号化して保存する場合はパスフレーズを指定、暗号化しない場合はパスフレーズを指定しない。  
暗号化した方が安全だが、その場合、SourceTreeを起動するときにパスフレーズの入力を求められる。暗号化しないと安全性が下がるが、SourceTreeを起動するときにパスフレーズの入力は求められない。

* パスフレーズを指定する場合は、「Key」の「Key passphrase」と「Confirm passphrase」にパスフレーズを入力する。

* 「Actions」の「Save the generated key」で「Save private key」をクリック。  
適当なフォルダにid_rsa.ppkという名前で保存する。仮に暗号化してあっても他人にファイルが流出しないように注意する。特にパスフレーズを指定しないで暗号化しなかった場合は流出したらアウト。


## 4. GitHubのアカウントを作成
* GitHubで検索し、[オフィシャルサイト](https://github.com/)にアクセス
* トップページでユーザー名、メール・アドレス、パスワードを指定して、サインアップする
* 「Choose your personal plan」で、「Free」が「Chosen」であることを確認し、「Finish sign up」をクリック
* メールが"「GitHub」 Please verify your email ..."といった件名で届くので、メール中のリンクをクリック
* 表示されたサイトで「Confirm」をクリック

## 5. GitHubにSSH Keyを登録
* SourceTreeを起動しておく
* 「ツール」→「SSHキーの作成/インポート」
* 「Load an existing private key file」で「Load」をクリックし、秘密鍵のファイルを指定する
* 「Key」の「Public key for pasting into OpenSSH authorized_keys file」の内容をコピーする

* GitHubのWebサイトで、右上の方にある「Account Settings」(工具のアイコン)をクリック
* 「SSH keys」を選択
* 「Add SSH Key」で「Title」は適当に、「Key」にSourceTreeからコピーした内容をペーストし、「Add key」をクリック

## 5. SourceTreeにGitHubアカウントを設定
* SourceTreeを起動しておく
* 「ファイル」→「セットアップウィザード」
* 「次へ」を繰り返していき、GitHubのアカウントを入力するところで、それを入力
