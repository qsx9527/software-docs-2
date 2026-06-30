# RK3568 快速开始占位文档

这是一份虚拟文档，用于测试 `qsx9527/software-docs-2` 仓库的手动拉取流程。

## 验证信息

- 远端仓库：`https://github.com/qsx9527/software-docs-2.git`
- 测试分支：`test/placeholder-docs`
- 文档路径：`zh/芯片文档/RK3568/quick-start.md`

看到这段内容，说明中文 RK3568 测试文档已经被拉取。

尝试mdx语法：
<span style={{ color: 'red', fontWeight: 700 }}>不要在虚拟机共享文件夹以及非英文目录存放、解压SDK，避免产生不必要的错误</span>



# MDX Sandbox for C40PL

这是一篇手动创建在 `zh/AI摄像机/C40PL/` 下的 `.mdx` 测试文档，用于验证当前 Fumadocs 生产服务对源 `.mdx` 文档的真实渲染效果。

<div className="not-prose rounded-lg border border-fd-border bg-fd-secondary/40 p-4">
  <p className="m-0 text-fd-primary font-semibold">这是一个小写 JSX/HTML 容器，使用 className 字符串属性。</p>
  <p className="m-0 text-fd-muted-foreground">这篇文档用于验证源 .mdx 只保留门户链接和图片重写，不再进入旧 Markdown 兼容清洗。</p>
</div>

## JSX 字符串属性

<div className="not-prose rounded-lg border border-fd-border bg-fd-secondary/40 p-4">
  <p className="m-0 text-fd-primary font-semibold">这一行使用 JSX 的 className 字符串属性。</p>
  <p className="m-0 text-fd-muted-foreground">字符串属性不依赖 JSX 表达式，适合作为基础对照组。</p>
</div>

## JSX style 对象

<div style={{ color: 'red', border: '1px solid currentColor', padding: '12px', borderRadius: '6px' }}>
  这一段使用 `style={{ color: 'red' }}`，如果 .mdx 没有进入旧 Markdown 兼容清洗，这里应该显示为红色。
</div>

行内红字：<span style={{ color: 'red', fontWeight: 700 }}>这段 span 也应该是红色</span>。

## Fumadocs 内置大写组件

<Cards>
  <Card title="站内链接" href="/docs/products/ai-camera/C40PL/getting-started/started" description="验证源 .mdx 中的大写组件不会被兼容清洗转义。" />
  <Card title="本页锚点" href="#mdx-sandbox-anchor" description="验证大写组件和普通锚点可以共存。" />
</Cards>

## 原生 HTML 与 MDX 混写

可以混用 <span className="text-fd-primary font-semibold">带 className 的 span</span>、<kbd>Ctrl</kbd> + <kbd>K</kbd>、<u>下划线</u>、H<sub>2</sub>O、E = mc<sup>2</sup>。

<details open>
  <summary>展开区域 summary</summary>

  这里是 `<details>` 内部内容，里面仍然可以写 **Markdown 加粗** 和列表：

  - 第一项
  - 第二项
</details>

## 表格

| 能力 | 写法 | 当前效果 |
| --- | --- | --- |
| Markdown 表格 | `table syntax` | 由 Fumadocs 包装成可横向滚动表格 |
| 大写 JSX 组件 | `<Cards>` / `<Card>` | .mdx 跳过兼容清洗后应作为组件渲染 |
| 字符串属性 | `className="..."` | 可渲染 |
| 花括号表达式 | `style={{ color: 'red' }}` | .mdx 跳过兼容清洗后应保留 JSX 表达式 |

## 图片

![C40PL](../../../rv1126_img/C40PL/c40pl.jpg)

## 锚点

<a id="mdx-sandbox-anchor"></a>

可以跳到 [本页锚点](#mdx-sandbox-anchor)，也可以跳到 [C40PL 快速开始](/docs/products/ai-camera/C40PL/getting-started/started)。

## 代码块

```mdx
<div className="not-prose rounded-lg border border-fd-border p-4">
  小写 HTML/JSX 标签可以在当前源文档链路里渲染。
</div>
```
