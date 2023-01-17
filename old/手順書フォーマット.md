<!-- omit in toc -->
# 2023-01-16  ConfigRules情報収集


## 1. このドキュメントの目次

- [1. ドキュメント作成者](#1-ドキュメント作成者)
- [2. 前提条件](#4-前提条件)
- [3. 作業者](#5-作業者)
- [4. 副作業者 (チェッカー)](#6-副作業者-チェッカー)
- [5. その他制約事項・備考](#7-その他制約事項備考)
- [6. 参考情報](#8-参考情報)
- [7. 手順書](#9-手順書)
  - [7.1. ログイン \[想定作業時間: 3分\]](#91-ログイン-想定作業時間-3分)
  - [7.2. ConfigRules情報取得作業 \[想定作業時間: 5分\]](#92-configrules情報取得作業-想定作業時間-5分)

## 2. 前提条件

- Config適合パックが1件以上デプロイされていること。

## 3. 作業者

## 4. 副作業者 (チェッカー)

## 5. その他制約事項・備考

## 6. 参考情報

## 7. 手順書

### 7.1. ログイン [想定作業時間: 3分]

- [x] [AWSマネージメントコンソールのURL](https://console.aws.amazon.com/console/home)をクリックする。
- [x] 以下の必要な情報を入力して`サインイン`をクリックする。
  - [x] アカウントID: `123456789012`
  - [x] ユーザー名: `xxxxxxxx`
  - [x] パスワード: `自分のIAMユーザーのパスワード`
- [ ] MFAコードを入力し、`送信`をクリックする。
- [ ] マネジメントコンソール上部に、**AWS マネジメントコンソール**を大きく表示されることを確認する。

### 7.2. ConfigRules情報取得作業 [想定作業時間: 5分]

- [ ] 「AWSマネジメントコンソール」画面上部のナビゲーションバーより「CloudShell」を検索し、CloudShellコンソール画面を表示する。  
  ![ConfigRules情報収集](./image/ConfigRules情報収集001.png)
  - [ ] CloudShellの画面が表示されることを確認する。  
  ![ConfigRules情報収集](./image/ConfigRules情報収集002.png)
- [ ] 「CloudShell」にて以下のコマンドを実行する。  

```txt
aws configservice describe-compliance-by-config-rule \
--query "ComplianceByConfigRules[].[\
ConfigRuleName,Compliance.ComplianceType,\
Compliance.ComplianceContributorCount.CappedCount,\
Compliance.ComplianceContributorCount.CapExceeded]" \
--compliance-types NON_COMPLIANT \
--output text | column -t  |grep conformance-pack > configrules.txt
```

- [ ] エラーとならないことを確認する。  

- [ ] 画面右上の「Actions」ボタンを押下し、「Download file」を押下する。
  - [ ] 「Download file」詳細画面が表示されることを確認する。
- [ ] 「Download file」詳細画面に「configrules.txt」を入力し、「Download」ボタンを押下する。
  - [ ] ダウンロードしたファイルが保存されていることを確認する。
  - [ ] ファイル名が「ConfigRules.txt」となっていること。
  
  ```txt
  ※「Download」ボタンを押下した際にエラーとなる場合、  
  configrules.txtの中身が空で0バイトとなっていること考えられます。  
  「cat」コマンドなどでconfigrules.txtファイルの中身をご確認ください。
  ```

- [ ] 保存したファイルを開いて確認する。ファイル名「ConfigRules.txt」を開く。
  - [ ] 選択した内容が保存されていることを確認する。
  - [ ] ファイル中に「NON_COMPLIAN」の文字が存在することを確認する。
