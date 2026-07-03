---
title: "software-docs-2 有 Frontmatter 无首部表格对照"
description: "用于验证 frontmatter title/description/icon 在没有文档首部测试表格时仍然生效。"
icon: "FileText"
---
# software-docs-2 有 Frontmatter 无首部表格对照

用于验证 frontmatter title/description/icon 在没有文档首部测试表格时仍然生效。

## 预期行为

- 页面标题来自 frontmatter.title。
- 页面描述来自 frontmatter.description。
- 左侧导航来自同目录 index.md，而不是 meta.json。
