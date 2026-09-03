# Changelog

[Keep a Changelog](https://keepachangelog.com/ja/1.1.0/) と [Semantic Versioning](https://semver.org/lang/ja/) に準拠する。

reusable workflow は `@main` 参照で全参照元へ即座に波及し、参照側は版を固定していない。変更内容は本ファイルで確認する。

## [Unreleased]

### Added

- Node と Python の reusable workflow（`reusable-node-ci.yml`、`reusable-python-ci.yml`）
- reusable workflow が参照する action の更新を受け取る dependabot 設定
- 本リポジトリの役割と参照関係を示す README
