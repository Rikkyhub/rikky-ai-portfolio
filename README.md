# Rikky AI Portfolio

AIを使って、曖昧な業務手順を**再現可能・検証可能・安全に止まれるWorkflow / Skill**へ変換するための公開ポートフォリオです。

実案件・個人プロジェクト本体のソースコードは公開せず、仕事上の能力を確認できるように一般化したサンプルだけを掲載しています。

## What I can do

- 既存の手順書・メモ・会話ログをAI実行用Workflow / Skillへ構造化
- input / output / completion criteria / stop conditionの明文化
- Human approvalが必要な境界の設計
- ChatGPT / Claude Code / Codexを使ったIssue → 実装 → Test → PR → Review運用
- AIが誤った前提で走り続けないためのfailure / escalation設計
- AIに任せる範囲を増やしつつ、人間の最終確認時間を減らす運用改善

## Featured samples

### 1. Structured Meeting Minutes Skill

人間向けの会議ログを、AIが毎回同じ基準で処理できるSkillへ落とした例です。

- [SKILL.md](samples/meeting-minutes-skill/SKILL.md)
- [Example input](samples/meeting-minutes-skill/example-input.md)
- [Expected output](samples/meeting-minutes-skill/example-output.md)

ポイント：

- 決定事項と提案を分離
- Owner / Deadlineを根拠なしに推測しない
- 情報不足は`TBD`またはEvidence gapとして残す
- 外部送信・カレンダー更新等はHuman approvalで止める

### 2. AI-assisted Issue → PR → Review workflow

AIに実装を任せてもscope driftや未検証のまま進まないようにする、GitHubベースの作業フロー例です。

- [Workflow example](workflows/issue-pr-review-example.md)

### 3. Human approval boundary

AIが自律実行してよい範囲と、人間承認が必要な操作を分離する設計例です。

- [Human approval example](safety/human-approval-example.md)

## Working principle

単に「AIにプロンプトを渡す」のではなく、次の状態を作ることを重視しています。

1. 何を入力として受け取るかが明確
2. 完了条件が明確
3. 不明点を勝手に推測しない
4. テスト可能
5. 危険・不可逆・外部送信操作では止まる
6. 別の人・別のAIでも再実行しやすい

## Typical delivery shape

既存の業務手順を受け取り、必要に応じて以下の形へ整理します。

```text
Current SOP / notes / transcript
        ↓
Goal / input / output整理
        ↓
AI Workflow / Skill
        ↓
Stop condition / Human approval境界
        ↓
Representative test
        ↓
Known limitations付きで納品
```

## Tools

ChatGPT / Claude Code / Codex / GitHub / Git / VS Code / CLI

## Public portfolio policy

このリポジトリには、顧客情報、勤務先情報、秘密情報、API key、private repositoryの内容、個人プロジェクト本体のソースコードは掲載しません。

掲載内容はポートフォリオ閲覧用です。別サイト・製品・テンプレート等への再利用を許可するものではありません。詳細は[LICENSE](LICENSE)を参照してください。
