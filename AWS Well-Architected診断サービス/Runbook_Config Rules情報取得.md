<!-- omit in toc -->
# 2023-01-16  ConfigRules情報収集

```txt
************* 概要 **************
本資料は、Well-Architecedと連携するConfigRulesの情報を
入手し、テキストファイルへ出力、格納するための操作手順である。
```

## 作業者（チーム名）
DTS運用チーム
## 前提条件、制約事項

- Config適合パックが1件以上デプロイされていること。

## 手順書[想定作業時間: 10分]

### 1. ログイン

1. [AWSマネージメントコンソールのURL](https://console.aws.amazon.com/console/home)をクリックする。
2. 以下の必要な情報を入力して`サインイン`をクリックする。
    1. アカウントID: `123456789012`
    2. ユーザー名: `xxxxxxxx`
    3. パスワード: `自分のIAMユーザーのパスワード`
3. MFAコードを入力し、`送信`をクリックする。
4. マネジメントコンソール上部に、**AWS マネジメントコンソール**を大きく表示されることを確認する。

### 2. ConfigRules情報取得作業

1. 「AWSマネジメントコンソール」画面上部のナビゲーションバーより「CloudShell」を検索し、CloudShellコンソール画面を表示する。  
 ![ConfigRules情報収集](./images/ConfigRules情報収集001.png)
    1. CloudShellの画面が表示されることを確認する。  
 ![ConfigRules情報収集](./images/ConfigRules情報収集002.png)
    2. CloudShellにて以下のコマンドを実行する。  
  
     ```txt
      aws configservice describe-compliance-by-config-rule \
      --query "ComplianceByConfigRules[].[\
      ConfigRuleName,Compliance.ComplianceType,\
      Compliance.ComplianceContributorCount.CappedCount,\
      Compliance.ComplianceContributorCount.CapExceeded]" \
      --compliance-types NON_COMPLIANT \
      --output text | column -t  |grep conformance-pack > configrules.txt
     ```  

2. 画面右上の「Actions」ボタンを押下し、「Download file」を押下する。  
    ![ConfigRules情報収集](./images/ConfigRules情報収集003.png)
    1. 「Download file」詳細画面が表示されることを確認する。
        ![ConfigRules情報収集](./images/ConfigRules情報収集004.png)

3. 「Download file」詳細画面に「configrules.txt」を入力し、「Download」ボタンを押下する。
![ConfigRules情報収集](./images/ConfigRules情報収集005.png)
    1. ダウンロードしたファイルが保存されていることを確認する。
    2. ファイル名が「ConfigRules.txt」となっていること。

         ```txt
         ※「Download」ボタンを押下した際にエラーとなる場合、  
         conf  igrules.txtの中身が空で0バイトとなっていること考えられます。  
         「cat」コマンドなどでconfigrules.txtファイルの中身をご確認ください。
         ```

    3. ファイル名と格納場所を選択し、「保存」ボタンを押下する。
     ![ConfigRules情報収集](./images/ConfigRules情報収集006.png)

4. 保存したファイルを開いて確認する。ファイル名「ConfigRules.txt」を開く。
   ![ConfigRules情報収集](./images/ConfigRules情報収集007.png)
    1. 選択した内容が保存されていることを確認する。
    2. ファイル中に「NON_COMPLIAN」の文字が存在することを確認する。
  
## 参考情報
