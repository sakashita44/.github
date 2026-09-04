# Changelog

変更を日付ごとに記録する。分類は [Keep a Changelog](https://keepachangelog.com/ja/1.1.0/) に倣う。

reusable workflow は `@main` 参照で全参照元へ即座に波及し、参照側は版を固定していない。参照元は自分の CI の中身が変わったことを知る手段を持たないため、変更内容は本ファイルで確認する。

## 2026-09-04

### Added

- project-standards の共通レイヤを本リポジトリへ展開した。整形とリントの設定、pre-commit のフック、`pre-commit run --all-files` を実行する CI が入る。実装言語を持たないリポジトリ向けの経路をそのまま使っている。あわせて既存ファイルを配布設定の整形結果へ揃え、dependabot の更新を 1 つの pull request へ集約する `groups` を加えた

### Changed

- Node の CI が整形とリントを `pre-commit run --all-files` で実行するようにした。`npm run lint` と `npm run format:check` の手順を置き換えている。project-standards がフックの実行基盤を全種別で pre-commit へ統一し、検査の内容を `.pre-commit-config.yaml` が一箇所で定めるようになったため。Python の CI と手順の並びが揃い、gitleaks や YAML 構文検査など npm スクリプトが持たない検査も Node のリポジトリで走る。型検査は pre-push ステージのフックであり `run --all-files` の対象外のため、独立した手順として残す

## 2026-09-03

### Added

- Node と Python の reusable workflow（`reusable-node-ci.yml`、`reusable-python-ci.yml`）
- reusable workflow が参照する action の更新を受け取る dependabot 設定
- 本リポジトリの役割と参照関係を示す README

### Changed

- ランタイムの版を参照元のファイルから読むようにした。`.python-version` があれば `uv python install` がその値に従い、`.nvmrc` があればその値を `actions/setup-node` へ渡す。どちらも無い場合だけ `python-version`、`node-version` の入力値を使う。従来は入力の既定値がそのまま使われ、参照元が版を上げても CI が追従しなかった
