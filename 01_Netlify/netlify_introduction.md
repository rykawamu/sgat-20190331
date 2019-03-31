# netlify入門

## Netlifyのアカウント登録

Netlifyの公式ページにアクセス。「Sign up」をクリック。

[公式ページ](https://www.netlify.com/)

サインアップ画面で、アカウント作成方法を選ぶ。（以降は、「GitHubアカウント」で作成しているのを前提として記載）

[サインアップページ](https://app.netlify.com/signup)


<img src="./images/01_2019-03-17_16.19.09.png" width="600">

GitHubアカウントによるNetlifyの認証。

<img src="./images/01_2019-03-17_16.20.07.png" width="600">

Netlifyにログイン。クイックスタートガイドが表示される。

<img src="./images/01_2019-03-17_16.20.29.png" width="600">

<img src="./images/01_2019-03-17_16.22.19.png" width="600">

<img src="./images/01_2019-03-17_16.22.31.png" width="600">

これで、Netlifyのアカウント登録が完了。


## リポジトリ作成

Netlifyと連携させる、GitHub上にリポジトリを作成する。

### リポジトリの完成イメージ

リポジトリの完成イメージは以下。

[リポジトリ完成イメージ](https://github.com/rykawamu/netlify-sample)

### リポジトリ作成作業

まず、GitHub上にリポジトリを作成。

リポジトリ名は「**netlify-sample**」などで、自分がわかるようにつければ良い。

<img src="./images/01_2019-03-17_16.28.34.png" width="600">


ソースの構成は以下のイメージ。

```
root
  ∟ public/
      ∟ index.html
```

index.htmlの内容は以下。

```
<html>
<body>
    <h1>Hello Netlify</h1>
</body>
</html>
```

なお、上記のコードは、以下のリポジトリに用意している。

https://github.com/rykawamu/netlify-sample

## Netlifyの設定

GitHubのリポジトリを、Netlifyと連携させる。

「New site from Git」ボタンをクリック。

<img src="./images/01_2019-03-17_16.43.52.png" width="600">

連携するGitプロバイダを選択する。（ここでは「GitHub」をクリック）

<img src="./images/01_2019-03-17_16.44.24.png" width="600">

連携の認証画面が出てくるので、「Authorize 〜」ボタンをクリック

<img src="./images/01_2019-03-17_16.45.20.png" width="600">

リポジトリを選択する画面の表示される

<img src="./images/01_2019-03-17_16.49.09.png" width="600">

リポジトリが表示されていない時は、「Configure Netlify on GitHub」をクリック。

<img src="./images/01_2019-03-17_16.51.08.png" width="600">

リポジトリを選択する。（権限があるものが表示される）

<img src="./images/01_2019-03-17_16.58.15.png" width="600">

リポジトリを選択する。全てのリポジトリにする（「All repositories」）か、任意のリポジトリ（「Select repositories」）を選択する。今回は任意のリポジトリで対応する。

<img src="./images/01_2019-03-17_16.59.47.png" width="600">

（※画面下に「Install」ボタンがある）

<img src="./images/01_2019-03-17_17.00.03.png" width="600">

連携するリポジトリが選択された状態で、「Install」をクリックする。

<img src="./images/01_2019-03-17_17.01.39.png" width="600">

連携するのにパスワードが表示される。

<img src="./images/01_2019-03-17_17.02.13.png" width="600">

Netlify上で、リポジトリがPickされる。

<img src="./images/01_2019-03-17_17.03.18.png" width="600">

ブランチを選択する。ここでは、「Master」ブランチを選択。

<img src="./images/01_2019-03-17_17.05.01.png" width="600">


Publish directoryには「public/」を入力する。そして、「Deploy site」をクリックする。

<img src="./images/01_2019-03-17_17.08.07.png" width="600">

デプロイ中の画面。

<img src="./images/01_2019-03-17_17.10.29.png" width="600">

URLをブラウザに貼り付けて開く。（URLはデプロイ完了画面に載っている。）

<img src="./images/01_2019-03-17_17.14.05.png" width="600">

一旦これで完了。**Nelify Fucttions** に続く。