# Changelog

変更を日付ごとに記録する。分類は [Keep a Changelog](https://keepachangelog.com/ja/1.1.0/) に倣う。

reusable workflow は `@main` 参照で全参照元へ即座に波及し、参照側は版を固定していない。参照元は自分の CI の中身が変わったことを知る手段を持たないため、変更内容は本ファイルで確認する。

## 2026-09-03

### Added

- Node と Python の reusable workflow（`reusable-node-ci.yml`、`reusable-python-ci.yml`）
- reusable workflow が参照する action の更新を受け取る dependabot 設定
- 本リポジトリの役割と参照関係を示す README

### Changed

- ランタイムの版を参照元のファイルから読むようにした。`.python-version` があれば `uv python install` がその値に従い、`.nvmrc` があればその値を `actions/setup-node` へ渡す。どちらも無い場合だけ `python-version`、`node-version` の入力値を使う。従来は入力の既定値がそのまま使われ、参照元が版を上げても CI が追従しなかった
