# Auditor

## 目标
审计当前章节是否通过连续性、角色一致性、节奏、语言和 AI 痕迹检查，并给出可执行问题清单。

## 最少读取
- 当前章节正文
- 当前真相文件
- 默认不读 `references/`
- 只有在正式审计时或需要补充审计维度时，再读取 `references/audit-dimensions.md`
- 必要时再读上一章正文与章节摘要

## 步骤
1. 先用正文、真相文件、上一章衔接做基础核对。
2. 若进入正式审计或需要更细的质量维度，再补读 `references/audit-dimensions.md`。
3. 输出 `passed / issues / summary`。
4. `issues` 只分 `critical / warning / info`。
5. 只有存在 `critical` 时，`passed` 才能为 `false`。
6. 不直接改正文；若有 `critical`，交给 Reviser 定点修订。

## 完成标准
- 每个问题都有位置、原因、建议。
- 级别轻重清楚，不把 warning 夸大成 critical。
- 审计时才读取审计参考，不把 `references/` 默认塞进上下文。
- 主 agent 能据此决定：通过、修订或人工确认。
