---
title: GitHub ActionsとQiita CLIで始める記事の自動投稿：セットアップから運用まで
tags:
  - GitHub Actions
  - Qiita CLI
  - 自動投稿
  - ワークフロー
  - 技術共有
private: false
updated_at: '2024-12-24T07:56:34+09:00'
id: 59baa174f71217eff0b9
organization_url_name: null
slide: false
ignorePublish: false
---
## はじめに
- GitHubとQiitaの連携のメリット
  GitHubとQiitaを連携させることで、コードの管理と技術情報の共有がスムーズに行えます。GitHub上で管理しているリポジトリの内容をQiitaに自動的に投稿することで、最新の情報を常に共有することができます。また、Qiitaのフォロワーに対しても、GitHubの更新情報を迅速に伝えることができるため、情報の拡散力が向上します。

- 記事自動投稿の概要
  記事自動投稿の仕組みは、GitHubのリポジトリに新しいコミットがプッシュされた際に、特定の条件に基づいてQiitaに記事を自動的に投稿するものです。これにより、手動で記事を投稿する手間が省け、効率的に情報を発信することができます。具体的には、GitHub ActionsやWebhookを利用して、コミット内容を解析し、Qiita APIを通じて記事を投稿します。

## 必要なツールの準備
- Node.jsのインストール
  Node.jsは、JavaScriptの実行環境です。GitHub ActionsやQiita CLIを利用するために必要です。Node.jsのインストール方法は、[公式サイト](https://nodejs.org/)からインストーラーをダウンロードし、指示に従ってインストールしてください。

- Qiita CLIのインストール
  Qiita CLIは、Qiitaに記事を投稿するためのコマンドラインツールです。Node.jsがインストールされている環境で、以下のコマンドを実行してインストールします。
  ```sh
  npm install -g qiita-cli
  ```
  インストール後、qiitaコマンドが使用できることを確認してください。

- GitHubリポジトリの作成
  Qiitaに投稿する記事の元となるコンテンツを管理するためのリポジトリを作成します。GitHubの公式サイトにアクセスし、新しいリポジトリを作成してください。リポジトリの名前や説明を入力し、公開または非公開の設定を行います。リポジトリが作成されたら、ローカル環境にクローンして作業を開始します。
  ```sh
  git clone https://github.com/your-username/your-repository.git
  cd your-repository
  ```
  これで、リポジトリの準備が完了です。

## Qiita CLIのセットアップ
- Qiita CLIの初期化と設定
  最新版のQiita CLIでは、`qiita init`コマンドを実行すると、自動的に`publish.yml`ファイルが作成されます。このファイルを使うことで、簡単にGitHub Actionsを設定できます。

  `qiita init`を実行して作成される`publish.yml`の内容は以下のとおりです。

  ```yaml
  # Please set 'QIITA_TOKEN' secret to your repository
  name: Publish articles

  on:
    push:
      branches:
        - main
        - master
    workflow_dispatch:

  permissions:
    contents: write

  concurrency:
    group: ${{ github.workflow }}-${{ github.ref }}
    cancel-in-progress: false

  jobs:
    publish_articles:
      runs-on: ubuntu-latest
      timeout-minutes: 5
      steps:
        - uses: actions/checkout@v4
          with:
            fetch-depth: 0
        - uses: increments/qiita-cli/actions/publish@v1
          with:
            qiita-token: ${{ secrets.QIITA_TOKEN }}
            root: "."
  ```

  上記の設定を使用することで、`main`または`master`ブランチにプッシュされた際にQiita記事が自動的に投稿されます。

- Qiitaアクセストークンの取得と設定
  Qiitaに記事を投稿するためには、Qiitaのアクセストークンが必要です。アクセストークンは、Qiitaの設定ページから取得できます。以下の手順でアクセストークンを取得し、GitHubリポジトリに設定します。
  1. Qiitaにログインし、アクセストークンの設定ページにアクセスします。
  2. 「新しくトークンを発行する」ボタンをクリックし、必要な権限を設定してトークンを発行します。
  3. 発行されたトークンをコピーし、GitHubのリポジトリ設定ページに移動して、以下の手順でシークレットとして登録します。
     - リポジトリの「Settings」 > 「Secrets and variables」 > 「Actions」を選択します。
     - 「New repository secret」をクリックし、名前を`QIITA_TOKEN`、値をコピーしたアクセストークンにして保存します。

## GitHub Actionsの設定
- リポジトリへのシークレット設定
  上記で説明したように、アクセストークンをGitHubリポジトリのシークレットに設定します。

- ワークフローファイルの確認
  `qiita init`によって作成された`publish.yml`が正しく動作するか確認します。必要に応じて、修正を加えてください。

## 記事の作成と管理
- ローカル環境でのMarkdown記事作成
  GitHubリポジトリ内で記事をMarkdown形式で作成します。記事は`./articles`ディレクトリ内に保存します。

- GitHubリポジトリでのバージョン管理
  作成した記事は、GitHubでバージョン管理を行います。記事の更新履歴を記録できるため、変更内容の追跡が容易です。

- プッシュによる自動投稿の流れ
  リポジトリに変更を加えた後、以下のコマンドで変更をプッシュします。
  ```sh
  git add .
  git commit -m "Update articles"
  git push origin main
  ```
  これにより、GitHub Actionsがトリガーされ、Qiitaに記事が投稿されます。

## 運用上の注意点
- 既存記事のダウンロードを避ける方法
  Qiita CLIで既存記事をダウンロードすると、不要なデータがリポジトリに追加される可能性があります。必要な記事のみを操作するように設定を工夫してください。

- エラー時の対処方法
  自動投稿に失敗した場合、GitHub Actionsのログを確認してエラー原因を特定します。必要に応じて設定を修正してください。

- セキュリティ上の考慮点
  アクセストークンを適切に管理し、漏洩しないように注意してください。また、リポジトリのアクセス権限を適切に設定し、不正アクセスを防止します。

## おわりに
- 導入後の効果と感想
  GitHub ActionsとQiita CLIを活用することで、記事投稿の効率が大幅に向上します。手動での投稿作業が不要になり、最新情報を迅速に共有できるようになります。

- 今後の展望
  この仕組みをさらに発展させて、他のプラットフォームへの自動投稿や、記事内容の自動生成にも挑戦してみてください。
