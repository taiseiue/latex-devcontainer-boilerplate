# Latex on DevContainer Boilerplate
DevContainer上でLaTex文章を書くリポジトリのボイラープレート

### What's this?

VS Codeで、LaTex文章の作成に必要な環境をDevContainerにまとめたものです。このリポジトリは、GitHubの[テンプレートリポジトリ](https://docs.github.com/ja/repositories/creating-and-managing-repositories/creating-a-template-repository)として動作します。

現在の環境は以下の通りです。(必要に応じて変更するといいでしょう。)

- uplatex
- upbibtex
- dvipdfmx
- mendex
- LaTeX Workshop
- テキスト校正くん

### Usage

\* 初めに、VS CodeにDevContainer拡張機能を導入する必要があります。

1. このリポジトリから、新しいリポジトリを作成します。
2. リポジトリをcloneして、VS Codeで開きます。
3. 右下にポップアップする「Reopen in Container」をクリックします。

> [!NOTE]
> `./.latexmkrc`はリポジトリ全体に適用されます。記事ごとに別々に設定する場合は、記事と同じディレクトリに`.latexmkrc`を配置します。
> 
> また、`./style`以下のstyファイルはリポジトリ全体で読み込めます。新たに追加した後はウィンドウを再読み込みしてください。

### Why did you make it?

大学の学生実験でのレポート提出に備えて作成しました。

### License
このボイラープレートは、[The MIT License](./LICENSE.txt)のもとで公開します。

Copyright (c) 2025 Taisei Uemura  
Released under the [MIT license](./LICENSE.txt)