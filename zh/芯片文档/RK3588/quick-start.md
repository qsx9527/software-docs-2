---
title: "software-docs-2 RK3588 quick-start 表格内容测试"
description: "用于验证 software-docs-2/RK3588/quick-start 的 frontmatter title、description 和 icon。"
icon: "Table"
---
# software-docs-2 RK3588 quick-start 表格内容测试

<!-- firefly-meta-test-table:start -->
| 字段 | 测试值 |
| --- | --- |
| frontmatter.title | software-docs-2 RK3588 quick-start 表格内容测试 |
| source repo | software-docs-2 |
| locale/category/product | zh/芯片文档/RK3588 |
| document | quick-start |
| frontmatter.description | 用于验证 software-docs-2/RK3588/quick-start 的 frontmatter title、description 和 icon。 |
| frontmatter.icon | Table |
<!-- firefly-meta-test-table:end -->


这是一份虚拟文档，用于测试 `qsx9527/software-docs-2` 仓库的手动拉取流程。

## 验证信息

- 远端仓库：`https://github.com/qsx9527/software-docs-2.git`
- 测试分支：`test/placeholder-docs`
- 文档路径：`zh/芯片文档/RK3588/quick-start.md`

看到这段内容，说明中文 RK3588 测试文档已经被拉取。


在这里，尝试一下引用跳转[查看 AIO-8550JD4 前言](/docs/products/mainboards/AIO-8550JD4/aio-8550jd4/preface)

这里尝试双中括号 
* [[开发使用文档]](../RK3568/index.md) 

这里尝试单中括号 
* [开发使用文档](../RK3568/index.md) 


这里尝试三中括号 
* [[[开发使用文档]]](../RK3568/index.md)


# Fumadocs (Framework Mode): Markdown
URL: /docs/markdown
Source: https://raw.githubusercontent.com/fuma-nama/fumadocs/refs/heads/main/apps/docs/content/docs/(framework)/markdown/index.mdx

How to write documents
        




## Introduction [#introduction]

Fumadocs provides many useful extensions to MDX, a markup language. Here is a brief introduction to the default MDX syntax of Fumadocs.

> MDX is not the only supported format of Fumadocs. In fact, you can use any renderer such as headless CMS.
>
> See [Custom Content Source](/docs/integrations/content/custom) for details.

## MDX [#mdx]

We recommend MDX, a superset of Markdown with JSX syntax.
It allows you to import components, and use them in the document, or even writing JavaScript.

See:

* [MDX Syntax](https://mdxjs.com/docs/what-is-mdx/#mdx-syntax).
* GFM (GitHub Flavored Markdown) is also supported, see [GFM Specification](https://github.github.com/gfm).

```mdx
import { Component } from './component';

<Component name="Hello" />

## Heading

### Heading

#### Heading

Hello World, **Bold**, _Italic_, ~~Hidden~~

1. First
2. Second
3. Third

- Item 1
- Item 2

> Quote here

![alt](/image.png)

| Table | Description |
| ----- | ----------- |
| Hello | World       |
```

### Frontmatter [#frontmatter]

Fumadocs support YAML-based frontmatter by default, `title` represents the page title (`h1`) in Fumadocs UI.

```mdx
---
title: This is a document
---

...
```

For this reason, h1 title (`# Heading`) is usually unused when writing Markdown/MDX unless you have custom logic for page title rendering.

<Callout title="In Fumadocs MDX">
  You can use the [`schema`](/docs/mdx/collections#schema-1) option to add frontmatter properties.
</Callout>

### Auto Links [#auto-links]

Internal links use the `<Link />` component of your React framework (e.g. `next/link`) to allow prefetching and avoid hard-reload.

External links will get the default `rel="noreferrer noopener" target="_blank"` attributes for security.

```mdx
[My Link](https://github.github.com/gfm)

This also works: https://github.github.com/gfm.
```

### Cards [#cards]

Useful for adding links.

```mdx
import { HomeIcon } from 'lucide-react';

<Cards>
  <Card
    href="https://nextjs.org/docs/app/building-your-application/data-fetching/fetching-caching-and-revalidating"
    title="Fetching, Caching, and Revalidating"
  >
    Learn more about caching in Next.js
  </Card>
  <Card title="href is optional">Learn more about `fetch` in Next.js.</Card>
  <Card icon={<HomeIcon />} href="/" title="Home">
    You can include icons too.
  </Card>
</Cards>
```

<Cards>
  <Card href="https://nextjs.org/docs/app/building-your-application/data-fetching/fetching-caching-and-revalidating" title="Fetching, Caching, and Revalidating">
    Learn more about caching in Next.js
  </Card>

  <Card title="href is optional">
    Learn more about 

    `fetch`

     in Next.js.
  </Card>

  <Card icon="<HomeIcon />" href="/" title="Home">
    You can include icons too.
  </Card>
</Cards>

#### "Further Reading" Section [#further-reading-section]

You can do something like:

```tsx title="page.tsx"
import { getPageTreePeers } from 'fumadocs-core/page-tree';
import { source } from '@/lib/source';

<Cards>
  {getPageTreePeers(source.getPageTree(), '/docs/my-page').map((peer) => (
    <Card key={peer.url} title={peer.name} href={peer.url}>
      {peer.description}
    </Card>
  ))}
</Cards>;
```

This will show the other pages in the same folder as cards.

<DocsCategory url="/docs/ui/navigation" />

### Callouts [#callouts]

Useful for adding tips/warnings, it is included by default. You can specify the type of callout:

* `info` (default)
* `warn`/`warning`
* `error`
* `success`
* `idea`

```mdx
<Callout>Hello World</Callout>

<Callout title="Title" type="warn">
  Hello World
</Callout>

<Callout title="Title" type="error">
  Hello World
</Callout>

<Callout title="Title" type="idea">
  Hello World
</Callout>
```

<Callout>
  Hello World
</Callout>

<Callout title="Title" type="warn">
  Hello World
</Callout>

<Callout title="Title" type="error">
  Hello World
</Callout>

<Callout title="Title" type="idea">
  Hello World
</Callout>

### Headings [#headings]

An anchor is automatically applied to each heading, it sanitizes invalid characters like spaces. (e.g. `Hello World` to `hello-world`)

```md
# Hello `World`
```

#### TOC Settings [#toc-settings]

The table of contents (TOC) will be generated based on headings, you can also customize the effects of headings:

```md
# Heading [!toc]

This heading will be hidden from TOC.

# Another Heading [toc]

This heading will **only** be visible in TOC, you can use it to add additional TOC items.
Like headings rendered in a React component:

<MyComp />
```

#### Custom Anchor [#custom-anchor]

You can add `[#slug]` to customize heading anchors.

```md
# heading [#my-heading-id]
```

You can also chain it with TOC settings like:

```md
# heading [toc] [#my-heading-id]
```

To link people to a specific heading, add the heading id to hash fragment: `/page#my-heading-id`.

### Codeblock [#codeblock]

Syntax Highlighting is supported by default using [Rehype Code](/docs/headless/mdx/rehype-code).

````mdx
```js
console.log('Hello World');
```

```js title="My Title"
console.log('Hello World');
```
````

#### Line Numbers [#line-numbers]

Show line numbers, it also works with Twoslash and other transformers.

<CodeBlockTabs defaultValue="Input">
  <CodeBlockTabsList>
    <CodeBlockTabsTrigger value="Input">
      Input
    </CodeBlockTabsTrigger>

    <CodeBlockTabsTrigger value="Output">
      Output
    </CodeBlockTabsTrigger>
  </CodeBlockTabsList>

  <CodeBlockTab value="Input">
    ````mdx
    ```ts twoslash lineNumbers
    const a = 'Hello World';
    //    ^?
    console.log(a); // [!code highlight]
    ```
    ````
  </CodeBlockTab>

  <CodeBlockTab value="Output">
    ```ts twoslash lineNumbers 
    const a = 'Hello World';
    //    ^?
    console.log(a); // [!code highlight]
    ```
  </CodeBlockTab>
</CodeBlockTabs>

You can set the initial value of line numbers.

<CodeBlockTabs defaultValue="Input">
  <CodeBlockTabsList>
    <CodeBlockTabsTrigger value="Input">
      Input
    </CodeBlockTabsTrigger>

    <CodeBlockTabsTrigger value="Output">
      Output
    </CodeBlockTabsTrigger>
  </CodeBlockTabsList>

  <CodeBlockTab value="Input">
    ````mdx
    ```js lineNumbers=4
    function main() {
      console.log('starts from 4');

      return 0;
    }
    ```
    ````
  </CodeBlockTab>

  <CodeBlockTab value="Output">
    ```js lineNumbers=4 
    function main() {
      console.log('starts from 4');

      return 0;
    }
    ```
  </CodeBlockTab>
</CodeBlockTabs>

#### Shiki Transformers [#shiki-transformers]

We support some of the [Shiki Transformers](https://shiki.style/packages/transformers), allowing you to highlight/style specific lines.

<CodeBlockTabs defaultValue="Input">
  <CodeBlockTabsList>
    <CodeBlockTabsTrigger value="Input">
      Input
    </CodeBlockTabsTrigger>

    <CodeBlockTabsTrigger value="Output">
      Output
    </CodeBlockTabsTrigger>
  </CodeBlockTabsList>

  <CodeBlockTab value="Input">
    ````md
    ```tsx
    // highlight a line
    <div>Hello World</div> // [\!code highlight]

    // highlight a word
    // [\!code word:Fumadocs]
    <div>Fumadocs</div>

    // diff styles
    console.log('hewwo'); // [\!code --]
    console.log('hello'); // [\!code ++]

    // focus
    return new ResizeObserver(() => {}) // [\!code focus]
    ```
    ````
  </CodeBlockTab>

  <CodeBlockTab value="Output">
    ```tsx
    // highlight a line
    <div>Hello World</div> // [!code highlight]

    // highlight a word
    // [!code word:Fumadocs]
    <div>Fumadocs</div>

    // diff styles:
    console.log('hewwo'); // [!code --]
    console.log('hello'); // [!code ++]

    // focus
    return new ResizeObserver(() => {}) // [!code focus]
    ```
  </CodeBlockTab>
</CodeBlockTabs>

#### Tab Groups [#tab-groups]

````mdx
```ts tab="Tab 1"
console.log('A');
```

```ts tab="Tab 2"
console.log('B');
```
````

<CodeBlockTabs defaultValue="Tab 1">
  <CodeBlockTabsList>
    <CodeBlockTabsTrigger value="Tab 1">
      Tab 1
    </CodeBlockTabsTrigger>

    <CodeBlockTabsTrigger value="Tab 2">
      Tab 2
    </CodeBlockTabsTrigger>
  </CodeBlockTabsList>

  <CodeBlockTab value="Tab 1">
    ```ts
    console.log('A');
    ```
  </CodeBlockTab>

  <CodeBlockTab value="Tab 2">
    ```ts
    console.log('B');
    ```
  </CodeBlockTab>
</CodeBlockTabs>

To add a persist ID, define `tab-group` at the first codeblock:

````mdx
```ts tab="Tab 1" tab-group="my-custom-group"
console.log('A');
```

```ts tab="Tab 2"
console.log('B');
```
````

<CodeBlockTabs defaultValue="Tab 1" groupId="my-custom-group">
  <CodeBlockTabsList>
    <CodeBlockTabsTrigger value="Tab 1">
      Tab 1
    </CodeBlockTabsTrigger>

    <CodeBlockTabsTrigger value="Tab 2">
      Tab 2
    </CodeBlockTabsTrigger>
  </CodeBlockTabsList>

  <CodeBlockTab value="Tab 1">
    ```ts  
    console.log('A');
    ```
  </CodeBlockTab>

  <CodeBlockTab value="Tab 2">
    ```ts
    console.log('B');
    ```
  </CodeBlockTab>
</CodeBlockTabs>

Another group:

<CodeBlockTabs defaultValue="Tab 1" groupId="my-custom-group">
  <CodeBlockTabsList>
    <CodeBlockTabsTrigger value="Tab 1">
      Tab 1
    </CodeBlockTabsTrigger>

    <CodeBlockTabsTrigger value="Tab 2">
      Tab 2
    </CodeBlockTabsTrigger>
  </CodeBlockTabsList>

  <CodeBlockTab value="Tab 1">
    ```ts  
    console.log('A');
    ```
  </CodeBlockTab>

  <CodeBlockTab value="Tab 2">
    ```ts
    console.log('B');
    ```
  </CodeBlockTab>
</CodeBlockTabs>

#### MDX in Tab Groups [#mdx-in-tab-groups]

While disabled by default, you use MDX in tab values by configuring the remark plugin:

<CodeBlockTabs defaultValue="Fumadocs MDX">
  <CodeBlockTabsList>
    <CodeBlockTabsTrigger value="Fumadocs MDX">
      Fumadocs MDX
    </CodeBlockTabsTrigger>

    <CodeBlockTabsTrigger value="MDX Compiler">
      MDX Compiler
    </CodeBlockTabsTrigger>
  </CodeBlockTabsList>

  <CodeBlockTab value="Fumadocs MDX">
    ```ts  title="source.config.ts"
    import { defineConfig } from 'fumadocs-mdx/config';

    export default defineConfig({
      mdxOptions: {
        remarkCodeTabOptions: {
          parseMdx: true, // [!code ++]
        },
      },
    });
    ```
  </CodeBlockTab>

  <CodeBlockTab value="MDX Compiler">
    ```ts
    import { compile } from '@mdx-js/mdx';
    import { remarkCodeTab } from 'fumadocs-core/mdx-plugins';

    await compile('...', {
      remarkPlugins: [
        [
          remarkCodeTab,
          {
            parseMdx: true, // [!code ++]
          },
        ],
      ],
    });
    ```
  </CodeBlockTab>
</CodeBlockTabs>

````mdx
```ts tab="<Building /> Tab 1"
console.log('A');
```

```ts tab="<Rocket /> Tab 2"
console.log('B');
```
````

<CodeBlockTabs defaultValue="<Building /> Tab 1">
  <CodeBlockTabsList>
    <CodeBlockTabsTrigger value="<Building /> Tab 1">
      <Building />

       Tab 1
    </CodeBlockTabsTrigger>

    <CodeBlockTabsTrigger value="<Rocket /> Tab 2">
      <Rocket />

       Tab 2
    </CodeBlockTabsTrigger>
  </CodeBlockTabsList>

  <CodeBlockTab value="<Building /> Tab 1">
    ```ts
    console.log('A');
    ```
  </CodeBlockTab>

  <CodeBlockTab value="<Rocket /> Tab 2">
    ```ts
    console.log('B');
    ```
  </CodeBlockTab>
</CodeBlockTabs>

### Include [#include]

> This is only available on **Fumadocs MDX**.

Reference another file (can also be a Markdown/MDX document).
Specify the target file path in `<include>` tag (relative to the MDX file itself).

```mdx title="page.mdx"
<include>./another.mdx</include>
```

See [other usages of include](/docs/mdx/include).

### NPM Commands [#npm-commands]

Useful for generating commands for installing packages with different package managers.

<CodeBlockTabs defaultValue="Input">
  <CodeBlockTabsList>
    <CodeBlockTabsTrigger value="Input">
      Input
    </CodeBlockTabsTrigger>

    <CodeBlockTabsTrigger value="Output">
      Output
    </CodeBlockTabsTrigger>
  </CodeBlockTabsList>

  <CodeBlockTab value="Input">
    ````md
    ```npm
    npm i next -D
    ```
    ````
  </CodeBlockTab>

  <CodeBlockTab value="Output">
    <CodeBlockTabs defaultValue="npm" groupId="package-manager">
      <CodeBlockTabsList>
        <CodeBlockTabsTrigger value="npm">
          npm
        </CodeBlockTabsTrigger>

        <CodeBlockTabsTrigger value="pnpm">
          pnpm
        </CodeBlockTabsTrigger>

        <CodeBlockTabsTrigger value="yarn">
          yarn
        </CodeBlockTabsTrigger>

        <CodeBlockTabsTrigger value="bun">
          bun
        </CodeBlockTabsTrigger>
      </CodeBlockTabsList>

      <CodeBlockTab value="npm">
        ```bash
        npm i next -D
        ```
      </CodeBlockTab>

      <CodeBlockTab value="pnpm">
        ```bash
        pnpm add next -D
        ```
      </CodeBlockTab>

      <CodeBlockTab value="yarn">
        ```bash
        yarn add next --dev
        ```
      </CodeBlockTab>

      <CodeBlockTab value="bun">
        ```bash
        bun add next --dev
        ```
      </CodeBlockTab>
    </CodeBlockTabs>
  </CodeBlockTab>
</CodeBlockTabs>

See [`remark-npm`](/docs/headless/mdx/remark-npm) for details.

### Steps [#steps]

Useful for denoting steps for guides, see [`remark-steps`](/docs/headless/mdx/remark-steps) for enable & configure.

```md
### Installation [step]

### Write Code [step]

### Deploy [step]
```

<div className="fd-steps">
  <div className="fd-step">
    #### Installation [#installation-step]
  </div>

  <div className="fd-step">
    #### Write Code [#write-code-step]
  </div>

  <div className="fd-step">
    #### Deploy [#deploy-step]
  </div>
</div>

### Other Components [#other-components]

You can configure & use the [built-in components](/docs/ui/components) in your MDX document, such as Tabs, Accordions and Zoomable Image.

## Additional Features [#additional-features]

You may be interested:

<DocsCategory />
