<!-- omit in toc -->
# 2023-01-17  RunBook管理

## 1.VSCode推奨プラグイン

| プラグイン                                                                         | 必須 | 説明                                                                                                                                      |
|-------------------------------------------------------------------------------|----|-----------------------------------------------------------------------------------------------------------------------------------------|
| Markdown All in One                                                           | 〇  | Markdown に必要なプラグインの多くが入っています。                                                                                                           |
| Markdownlint                                                                      | 〇  | MMarkdownの構文やスタイルをチェックしてくれるVS Code拡張機能  です。                                                                                                          |
| Markdown Preview Enhanced                                                                      | 〇  | Markdownのプレビュー及び、HTMLへのエクスポートの拡張機能です。                                                                                                            |
| Text Table                                                                    | 〇  | Markdown 内でのテーブル作成が容易になります。Ctrl+Shipt+Pで Command Pallet を起動してcreate tableを選択してn*n指定でテーブルフォーマットが作れたり、Ctrl+Q２回押下で Table Mode になって編集ができます。 |
| Paste Image                                                                    | 〇  | クリップボードに保存した画像をCtrl+Alt+Vでそのままファイル化及び画像埋め込みで Markdown 内に埋め込みができます。 |
| Code Spell Checker                                                                    |   | Markdown 内でのスペルチェックを行います。 |
| テキスト校正くん Checker                                                                    |   | Markdown 内での日本語のチェックを行います。 |

## 2.基本ディレクトリ構成

```txt
.
┝ .vscode
│　└runbook：手順書管理.mdや手順書フォーマット.md、手順書サンプル.md を格納。
│　　└ XXX : runbookの名称をフォルダ名とし、mdファイルを格納する。ファイル名はXXXと同一とする。
│　　　└ image : XXXのrunbook内で使用される図、表など画像データを格納する。ファイル名は任意。
│　　└ YYY : runbookの名称をフォルダ名とし、mdファイルを格納する。ファイル名はYYYと同一とする。
│　　　└ image : YYYのrunbook内で使用される図、表など画像データを格納する。ファイル名は任意。


```