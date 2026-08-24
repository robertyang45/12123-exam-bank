# 12123 学法减分 · 共享题库

本仓库是 [12123-exam-helper](https://github.com/)（WorkBuddy 技能）的**协同题库**。
每位考生答题后把遇到的新题推回这里，题库随使用人数自然增长，命中率与准确率随之提升。

## 题库结构

`bank.json`：

```json
{
  "meta": { "total": 37, "last_exam": "2026-08-24", "accuracy": 0.95 },
  "questions": [
    {
      "id": "Q001",
      "type": "single",            // single | multi | judge
      "category": "礼让通行",
      "question": "题干……",
      "options": ["A …", "B …"],
      "answer": "D",
      "explanation": "要点……",
      "keywords": ["关键词1", "关键词2"],
      "verified": true,            // 是否经官方答案确认
      "wrong_count": 0,            // 被官方纠正的次数
      "source_date": "2026-08-24"
    }
  ]
}
```

## 与技能如何协同

技能内置 `scripts/sync_bank.py`：

- 开考 `pull`：从本仓库的 raw 地址拉取并合并进本地（`wrong_count` 取较大值、新增题补入）。
- 考后 `push`：把本地新增题推回本仓库（有写权限则自动 commit+push，否则打印新增题供提 PR）。

## 如何贡献

- **有写权限**（协作者）：技能考后会自动推送，无需手动操作。
- **无写权限**：技能会打印新增题 JSON，复制后提 Pull Request 合入即可。
- 合并规则以 `id` 为主键，重复题取 `wrong_count` 较大者，不会丢失题目。

## 原始地址（供 BANK_URL 配置）

```
https://raw.githubusercontent.com/<owner>/12123-exam-bank/main/bank.json
```

将 `<owner>` 替换为仓库所属 GitHub 用户名。
