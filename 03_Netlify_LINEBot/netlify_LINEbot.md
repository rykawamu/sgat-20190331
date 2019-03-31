# LINE Bot開発

## LINE Developers のプロバイダーとチャネルの作成

以下、LINE Developersのアカウントがあり、LINE Developersにログインしている前提で記述しています。

### チャネルの新規作成

メニューから「プロバイダーリスト」を選択。「新規プロバイダー作成」をクリックして、プロバイダーを作成します。プロバイダー名は任意の名前で良いです。（既存のプロバイダーを利用しても構いません）

<img src="./images/03_2019-03-24_22.25.37.png" width="600">

プロバイダー作成後、プロバイダー名をクリックして、配下に登録されているチャネルの一覧を表示します。チャネルがない場合は、「新規チャネル作成」をクリック。

<img src="./images/03_2019-03-24_22.26.49.png" width="600">

「新規チャネル作成」をクリックすると、ポップアップが表示されるので「**Messaging API**」をクリック。

<img src="./images/03_2019-03-24_22.27.01.png" width="600">

チャネル登録画面（その１）

<img src="./images/03_2019-03-24_22.28.46.png" width="600">

チャネル登録画面（その２）

<img src="./images/03_2019-03-24_22.28.59.png" width="600">

チャネル登録画面（その３）

<img src="./images/03_2019-03-24_22.29.09.png" width="600">

アイコン、アプリ名、アプリの説明を入力。**アプリ名**は、そのままLINE Botにした時の「友達の名前」になります。

<img src="./images/03_2019-03-24_22.32.52.png" width="600">

プランは、**Developers Trial**で良いです。

なお、フリープランとの違いは、以下。

* Developers Trial : Push messageも使えるが、友達50人まで。
* フリー : 友達が無制限だが、Push messageは使えない。

<img src="./images/03_2019-03-24_22.34.17.png" width="600">

利用規約が表示される。

<img src="./images/03_2019-03-24_22.35.42.png" width="600">

利用規約を全部読んで（下までいって）、「同意する」ボタンをクリック。

<img src="./images/03_2019-03-24_22.36.15.png" width="600">

チャネルの確認画面（その１）

<img src="./images/03_2019-03-24_22.36.27.png" width="600">

チャネルの確認画面（その２）

<img src="./images/03_2019-03-24_22.36.41.png" width="600">

チャネルの確認画面（その３）

ここで「作成」をクリックして完了となる。

<img src="./images/03_2019-03-24_22.36.55.png" width="600">

チャネル一覧に、作成したチャネルが登録されている。

<img src="./images/03_2019-03-24_22.37.28.png" width="600">

作成したチャネルをクリックしたら、画面の一番下に「QRコード」があるので、それをLINE端末で読み取って友達になる。

<img src="./images/03_2019-03-24_22.38.17.png" width="600">

一旦、LINE Developers側の設定は終わり。

## Netlify側の準備

LINE Bot用の新しいリポジトリをGitHub上に作成する。

作成イメージを以下のGitHubに用意しました。

https://github.com/rykawamu/netlify-linebot-sample

ソースコードは上のリポジトリで紹介するので、ここでは記載しません。

利用するコードは、以下の二つになります。

* ping.js : 接続確認のためのコード
* reply.js : LINE Botとして応答してくれるコード

なお、reply.jsでは「**axios**」というライブラリを利用します。ローカルで確認する場合、以下のように「axios」をインストールする。

```
$ npm install --save axios
```

<img src="./images/03_2019-03-24_22.52.11.png" width="600">

Netlify側でも、新しいサイト（Sites）を準備。

<img src="./images/03_2019-03-24_23.11.33.png" width="600">

準備1。

<img src="./images/03_2019-03-24_23.14.27.png" width="600">

準備2。

<img src="./images/03_2019-03-24_23.14.47.png" width="600">

準備3。

<img src="./images/03_2019-03-24_23.16.54.png" width="600">

準備4。

<img src="./images/03_2019-03-24_23.17.14.png" width="600">

準備5。対象のリポジトリ（画像だと「**netlify-linebot-sample**」）を選択してデプロイを実施。

<img src="./images/03_2019-03-24_23.18.46.png" width="600">

Netlifyで「Functions」を確認。

ping.jsをクリック。

<img src="./images/03_2019-03-24_23.55.48.png" width="600">

Endpoint のURLが表示されるので、それをコピー。

<img src="./images/03_2019-03-24_23.56.07.png" width="600">

上でコピーしたURLをブラウザに貼り付けて実行。jsonデータが返ってくる。

<img src="./images/03_2019-03-24_23.58.00.png" width="600">

## LINE Botを使うためのチャネルの設定

再びLineDevelopers側の設定。

先ほど新規に作成したチャネルをクリック。

<img src="./images/03_2019-03-24_22.37.52.png" width="600">

設定の変更をする。

変更前：

* Webhook: 利用しない
* Webhook URL: 未設定

<img src="./images/03_2019-03-25_0.00.13.png" width="600">

それぞれ、横にある「編集」ボタンをクリックして、設定を変更する。

変更後：

* Webhook: **利用する**
* Webhook URL: *利用するURLを入力。*

<img src="./images/03_2019-03-25_0.00.46.png" width="600">

接続確認の実施。成功可否が表示される。

<img src="./images/03_2019-03-25_0.01.19.png" width="600">

Netlify側のFunctionログを見てみると、ログデータが表示されている。


<img src="./images/03_2019-03-25_0.03.57.png" width="600">


再び、LINE Developers側で「**アクセストークン**」を発行する。

<img src="./images/03_2019-03-25_0.04.46.png" width="600">

「再発行」をクリックする。

<img src="./images/03_2019-03-25_0.06.00.png" width="600">

「**アクセストークン**」が発行される。この値をコピーする。

<img src="./images/03_2019-03-25_0.06.21.png" width="600">

「Deploys」で「Deploy settings」をクリック。

<img src="./images/03_2019-03-25_0.29.53.png" width="600">

「Build & deploy」をクリックして、「**Build environment variables**」に環境変数を設定する。

* Key: **CHANNEL_TOKEN**
* Value: コピーしたアクセストークンを設定。

<img src="./images/03_2019-03-25_0.35.55.png" width="600">

「Functions」から「reply.js」を選択。

<img src="./images/03_2019-03-25_0.46.44.png" width="600">

EndpointのURLをコピー。

<img src="./images/03_2019-03-25_0.46.56.png" width="600">

LINEのチャネル側の「Webhook URL」をpingから**`コピーしたreply`**のURLへ変更。

<img src="./images/03_2019-03-25_0.49.38.png" width="600">

この状態で、友達になったLINE Botに話しかけると、LINE Botが「**Hello Netlify Bot**」と返してくれる。

あとは、GitHubリポジトリに登録されている別のFunctionsのURLを指定するなどして動作確認してみてください。

* quickReplay.js
* game.js

今回はここまで。