# .github

sakashita44 の全リポジトリに対する既定ファイルを提供するリポジトリ。

- `.github/ISSUE_TEMPLATE/`, `.github/PULL_REQUEST_TEMPLATE.md`: リポジトリが自身のテンプレートを持たない場合に GitHub が自動適用する。適用先の visibility は問わない
- `.github/workflows/reusable-*.yml`: 各リポジトリの CI から `uses:` で参照される reusable workflow。呼び出し側の caller は project-standards が配布する

設定ファイルの正本と展開手順は [project-standards](https://github.com/sakashita44/project-standards) を参照。
