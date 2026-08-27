# Rikky AI Portfolio

AIを使って、曖昧な業務手順を**再現可能・検証可能・安全に止まれるWorkflow / Skill**へ変換するための公開ポートフォリオです。

このリポジトリでは、実案件・個人プロジェクトのソースコードを公開するのではなく、仕事上の能力を確認できるように一般化したサンプルだけを掲載します。

## What I can do

- 既存の手順書・メモ・会話ログをAI実行用Workflow / Skillへ構造化
- input / output / completion criteria / stop conditionの明文化
- Human approvalが必要な境界の設計
- ChatGPT / Claude Code / Codexを使ったIssue → 実装 → Test → PR → Review運用
- AIが誤った前提で走り続けないためのfailure / escalation設計
- AIに任せる範囲を増やしつつ、人間の最終確認時間を減らす運用改善

## Samples

このリポジトリには、順次以下の一般化サンプルを追加します。

- `samples/meeting-minutes-skill/` — 会議ログから決定事項・Action Item・期限を構造化するSkill
- `workflows/issue-pr-review-example.md` — AIを使ったIssue → PR → Reviewの再現可能な作業フロー
- `safety/human-approval-example.md` — AIが自律実行してよい範囲とHuman approval境界の例

## Working principle

単に「AIにプロンプトを渡す」のではなく、次の状態を作ることを重視しています。

1. 何を入力として受け取るかが明確
2. 完了条件が明確
3. 不明点を勝手に推測しない
4. テスト可能
5. 危険・不可逆・外部送信操作では止まる
6. 別の人・別のAIでも再実行しやすい

## Tools

ChatGPT / Claude Code / Codex / GitHub / Git / VS Code / CLI

## Public portfolio policy

このリポジトリには、顧客情報、勤務先情報、秘密情報、API key、private repositoryの内容、個人プロジェクト本体のソースコードは掲載しません。

掲載内容はポートフォリオ閲覧用です。別サイト・製品・テンプレート等への再利用を許可するものではありません。
