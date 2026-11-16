---
title: "レッスン 12 - GitHub Pages でサイトをデプロイする"
description: "GitHub Copilot app を使って Pages ワークフローを設定し、その pull request をレビューして、公開された Space Quiz を確認します。"
authors:
  - jamesmontemagno
lastUpdated: 2026-10-12
---

GitHub Pages に Space Quiz をデプロイして、誰でも利用できるようにします。Copilot はワークフローを準備し、デプロイを案内できますが、変更をレビューしてサイトが公開されたことを確認するのはユーザーの責任です。

このレッスンでは、次の操作を行います。

- Copilot に GitHub Pages のデプロイ設定を依頼します。
- マージする前にワークフローと pull request をレビューします。
- デプロイの進行を確認し、公開されたサイトを検証します。

## シナリオ

Space Quiz はすでに GitHub リポジトリにありますが、手軽に試す方法がまだありません。1 ファイルのサイトを GitHub Pages で公開すると、サーバーやランタイム依存関係を追加せずに、公開 URL からアクセスできるようになります。

## Copilot にデプロイの準備を依頼する

> [!WARNING]
> pull request を作成すると、コードがコミットおよびプッシュされることがあります。このプロンプトを送る前に、承認設定と送信先リポジトリを確認してください。**Approve all** が選択されている場合、別の確認プロンプトが表示されるとは限りません。

`space-quiz` の Copilot app セッションで、次のプロンプトを送信します。

```plaintext
このリポジトリの GitHub Pages デプロイを準備してください。必要であれば Web サイトをビルドし、変更がデフォルトブランチに反映された後に GitHub Pages にデプロイする GitHub Actions ワークフローを作成してください。README がまだない場合は、アプリの説明とローカルでの実行方法を記載した README を追加してください。これらの変更を含む pull request を作成し、そのリンクと必要な Pages の設定または権限を報告してください。マージ、自動マージの有効化、Pages の設定変更、デプロイは行わないでください。作業を停止して、レビューを待ってください。
```

## ワークフローと pull request をレビューする

1. README がリポジトリにまだ存在しない場合に限り、追加されていることを確認します。
2. ワークフローのビルドとデプロイの手順、トリガー、権限など、pull request の変更をレビューします。
3. マージされていない pull request ではなく、デフォルトブランチからデプロイすることを確認します。
4. 必要な修正を依頼し、更新された diff をレビューします。マージを許可する前に、必須の pull request チェックが成功するまで待ちます。

## マージとデプロイを許可する

> [!WARNING]
> 次のプロンプトは、レビュー済みの pull request のマージ、リポジトリの Pages 設定の変更、サイトの公開をエージェントに許可します。レビューを完了し、リポジトリと pull request を確認した後にのみ送信してください。承認設定によっては、別の確認プロンプトなしでこれらの操作が実行されることがあります。

`<PR_NUMBER>` をレビューした pull request の番号に置き換えて、このプロンプトを別途送信します。

```plaintext
このリポジトリの pull request <PR_NUMBER> をレビューし、マージとデプロイを許可します。GitHub Actions を使うように GitHub Pages を有効にし、必須チェックの成功後に限り、その pull request だけをマージしてください。デプロイが成功するまで監視し、公開された Web サイトの最終 URL を報告してください。Pages の有効化やマージに必要な権限がない場合は、私が何を承認または実行する必要があるかを正確に伝えてください。サイトが実際に公開されるまでは、成功したと報告しないでください。
```

![3 段階の図: space-quiz の pull request がマージされた状態、Build website・Upload artifact・Deploy to Pages の各ステップが成功した GitHub Actions の Deploy website 実行、yourname.github.io/space-quiz/ で公開された Space Quiz。](../../../_images/first-steps-app-pages-deploy.svg)

## デプロイを確認する

1. GitHub Actions のデプロイ実行が成功するまで確認します。
2. 報告された URL を開き、Space Quiz が読み込まれることを確認します。

エージェントが Pages を有効にしたり pull request をマージしたりできない場合は、提示された具体的な手順に従います。デプロイが成功し、公開サイトが読み込まれるまでは、作業を完了したと見なさないでください。

## まとめと次のステップ

Space Quiz を公開サイトとして利用できるようにし、エージェントの報告に頼らずデプロイを確認しました。次は[レッスン 13: レビューと次のステップ][next-lesson]に進みます。

[next-lesson]: ../13-review/
