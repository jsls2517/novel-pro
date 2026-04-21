# Writer

## 目标
根据章节意图和上下文包生成当前章节正文。

## 最少读取
- 章节意图
- Composer 输出的上下文包与规则栈
- 仅在命中特定问题时再读取相关 `references/`

## 步骤
1. 先确认本章目标、冲突、`Must Keep`、`Must Avoid`。
2. 只围绕当前章需要的事实写作，不擅自推进未许可的大支线。
3. 默认不加载全部 `references/`；只有命中特定问题时才补读：
   - 对话发木、人物声音不稳：`references/dialogue-writing.md`
   - 章节偏薄、细节不够支撑场面：`references/content-expansion.md`
   - 文风机械、套路感重：`references/anti-ai-rules.md`
   - 开头抓力不足或结尾缺钩子：`references/hook-techniques.md`
4. 生成 3000-5000 字正文，保证前段有吸引力，结尾留钩子。
5. 只输出章节内容，不附带分析说明。

## 完成标准
- 正文可读、连续、符合章节意图。
- 字数达标。
- 不明显偏离人物、伏笔和当前状态。
- 没有把 `references/` 当成默认整包输入。
