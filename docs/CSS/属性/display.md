# `display`

## 简介 (Introduction)

`display` 属性用于指定元素的显示类型，它决定了元素在页面布局中的行为方式（例如，是块级元素还是行内元素）。

## 语法 (Syntax)

`display` 属性可以接受多种关键字作为值，这些值可以分为六类。

```css
/* <display-outside> values */
display: block;
display: inline;

/* <display-inside> values */
display: flow;
display: flow-root;
display: table;
display: flex;
display: grid;
display: ruby;

/* <display-listitem> values */
display: list-item;

/* <display-internal> values */
display: table-row-group;
display: table-header-group;
display: table-footer-group;
display: table-row;
display: table-cell;
display: table-column-group;
display: table-column;
display: table-caption;
display: ruby-base;
display: ruby-text;
display: ruby-base-container;
display: ruby-text-container;

/* <display-box> values */
display: contents;
display: none;

/* <display-legacy> values (pre-Level 3) */
display: inline-block;
display: inline-table;
display: inline-flex;
display: inline-grid;

/* 全局值 */
display: inherit;
display: initial;
display: revert;
display: revert-layer;
display: unset;
```

现代 CSS 语法（Level 3）将 `display` 属性分解为两个部分：外部显示类型（`display-outside`）和内部显示类型（`display-inside`），尽管浏览器仍然完美支持像 `inline-block` 这样的旧式单值语法。

-   **`display-outside`**: 定义元素如何与流中的其他元素交互（如 `block` 或 `inline`）。
-   **`display-inside`**: 定义其子元素的布局方式（如 `flow`、`grid` 或 `flex`）。

例如，`display: block;` 实际上是 `display: block flow;` 的简写。`display: inline-flex;` 是 `display: inline flex;` 的简写。

## 核心用法与示例 (Core Usage & Examples)

以下是 `display` 属性最常见值的核心用法。

---

!!! example "display: block"

    `block` 值使元素成为块级元素。它会占据其父元素容器的整个宽度，并在前后自动换行。`width` 和 `height` 属性可以生效。

    <div style="font-family: sans-serif; border: 2px dashed #ccc; padding: 10px;">
      <p style="background-color: #e0f7fa; border: 1px solid #00bcd4; margin: 5px 0; padding: 10px;">我是一个段落 (p)，默认就是 block。</p>
      <div style="background-color: #e0f7fa; border: 1px solid #00bcd4; margin: 5px 0; padding: 10px;">我是一个 div，默认也是 block。</div>
      <span>我是一个 span，</span>
      <span style="display: block; background-color: #ffcdd2; border: 1px solid #f44336; margin: 5px 0; padding: 10px;">但我被设置成了 display: block。</span>
    </div>

    <details>
    <summary>点击查看源码</summary>

    ```html
    <div>
      <p>我是一个段落 (p)，默认就是 block。</p>
      <div>我是一个 div，默认也是 block。</div>
      <span>我是一个 span，</span>
      <span class="block-span">但我被设置成了 display: block。</span>
    </div>
    ```

    ```css
    p, div {
      background-color: #e0f7fa;
      border: 1px solid #00bcd4;
      margin: 5px 0;
      padding: 10px;
    }
    .block-span {
      display: block;
      background-color: #ffcdd2;
      border: 1px solid #f44336;
      margin: 5px 0;
      padding: 10px;
    }
    ```

    </details>

---

!!! example "display: inline"

    `inline` 值使元素成为行内元素。它不会导致换行，宽度和高度由其内容决定。`width`, `height`, `margin-top`, `margin-bottom` 属性对 `inline` 元素无效。

    <div style="font-family: sans-serif; border: 2px dashed #ccc; padding: 10px; line-height: 2;">
      <div style="display: inline; background-color: #e0f7fa; border: 1px solid #00bcd4; padding: 5px; margin: 20px;">这是一个 div，但被设为 inline。</div>
      <span style="background-color: #ffcdd2; border: 1px solid #f44336; padding: 5px;">我是一个 span，默认就是 inline。</span>
      <strong style="background-color: #c8e6c9; border: 1px solid #4caf50; padding: 5px;">我也是 inline。</strong>
      <span>请注意，div 上的 `margin-top` 和 `margin-bottom` 没有生效。</span>
    </div>

    <details>
    <summary>点击查看源码</summary>

    ```html
    <div>
      <div class="inline-div">这是一个 div，但被设为 inline。</div>
      <span>我是一个 span，默认就是 inline。</span>
      <strong>我也是 inline。</strong>
      <span>请注意，div 上的 `margin-top` 和 `margin-bottom` 没有生效。</span>
    </div>
    ```

    ```css
    .inline-div {
      display: inline;
      background-color: #e0f7fa;
      border: 1px solid #00bcd4;
      padding: 5px;
      /* 上下 margin 无效，左右有效 */
      margin: 20px;
    }
    span, strong {
      background-color: #ffcdd2;
      border: 1px solid #f44336;
      padding: 5px;
    }
    strong {
      background-color: #c8e6c9;
      border: 1px solid #4caf50;
    }
    ```
    </details>

---

!!! example "display: inline-block"

    `inline-block` 是 `block` 和 `inline` 的结合体。元素在行内排列（像 `inline`），但可以设置宽度、高度和垂直方向的 margin/padding（像 `block`）。

    <div style="font-family: sans-serif; border: 2px dashed #ccc; padding: 10px;">
      <div style="display: inline-block; width: 100px; height: 80px; background-color: #e0f7fa; border: 1px solid #00bcd4; margin: 10px;">块 1</div>
      <div style="display: inline-block; width: 120px; height: 80px; background-color: #ffcdd2; border: 1px solid #f44336; margin: 10px;">块 2</div>
      <div style="display: inline-block; width: 80px; height: 80px; background-color: #c8e6c9; border: 1px solid #4caf50; margin: 10px;">块 3</div>
    </div>

    <details>
    <summary>点击查看源码</summary>

    ```html
    <div>
      <div class="box">块 1</div>
      <div class="box">块 2</div>
      <div class="box">块 3</div>
    </div>
    ```

    ```css
    .box {
      display: inline-block;
      height: 80px;
      background-color: #e0f7fa;
      border: 1px solid #00bcd4;
      margin: 10px;
      color: #333;
    }
    .box:nth-of-type(1) { width: 100px; }
    .box:nth-of-type(2) { width: 120px; background-color: #ffcdd2; border-color: #f44336;}
    .box:nth-of-type(3) { width: 80px; background-color: #c8e6c9; border-color: #4caf50; }
    ```    </details>

---

!!! example "display: flex"

    `flex` 将元素变为一个 flex 容器，其直接子元素（flex 项）将根据 Flexbox 布局模型进行排列。这是创建一维（行或列）布局的强大现代方法。

    <div style="font-family: sans-serif; border: 2px dashed #ccc; padding: 10px;">
      <div style="display: flex; justify-content: space-around; align-items: center; background-color: #f3e5f5; height: 100px; padding: 10px;">
        <div style="background-color: #e1bee7; padding: 15px; border: 1px solid #8e24aa;">项目 1</div>
        <div style="background-color: #e1bee7; padding: 25px; border: 1px solid #8e24aa;">项目 2</div>
        <div style="background-color: #e1bee7; padding: 10px; border: 1px solid #8e24aa;">项目 3</div>
      </div>
    </div>

    <details>
    <summary>点击查看源码</summary>

    ```html
    <div class="flex-container">
      <div class="flex-item">项目 1</div>
      <div class="flex-item">项目 2</div>
      <div class="flex-item">项目 3</div>
    </div>
    ```

    ```css
    .flex-container {
      display: flex;
      justify-content: space-around; /* 水平分布 */
      align-items: center;          /* 垂直居中 */
      background-color: #f3e5f5;
      height: 100px;
      padding: 10px;
    }

    .flex-item {
      background-color: #e1bee7;
      border: 1px solid #8e24aa;
    }
    .flex-item:nth-of-type(1) { padding: 15px; }
    .flex-item:nth-of-type(2) { padding: 25px; }
    .flex-item:nth-of-type(3) { padding: 10px; }
    ```
    </details>

---

!!! example "display: grid"

    `grid` 将元素变为一个 grid 容器，其直接子元素可以按照二维（行和列）网格进行布局。这是最强大的 CSS 布局系统，适用于复杂的页面布局。

    <div style="font-family: sans-serif; border: 2px dashed #ccc; padding: 10px;">
      <div style="display: grid; grid-template-columns: 1fr 2fr; grid-gap: 10px; background-color: #e3f2fd; padding: 10px;">
        <div style="background-color: #bbdefb; padding: 20px; border: 1px solid #1976d2; grid-column: 1 / 2; grid-row: 1 / 3;">侧边栏</div>
        <div style="background-color: #bbdefb; padding: 20px; border: 1px solid #1976d2;">主内容 1</div>
        <div style="background-color: #bbdefb; padding: 20px; border: 1px solid #1976d2;">主内容 2</div>
      </div>
    </div>

    <details>
    <summary>点击查看源码</summary>

    ```html
    <div class="grid-container">
      <div class="grid-item sidebar">侧边栏</div>
      <div class="grid-item">主内容 1</div>
      <div class="grid-item">主内容 2</div>
    </div>
    ```

    ```css
    .grid-container {
      display: grid;
      grid-template-columns: 1fr 2fr; /* 两列，第二列是第一列宽度的2倍 */
      grid-gap: 10px; /* 网格间隙 */
      background-color: #e3f2fd;
      padding: 10px;
    }

    .grid-item {
      background-color: #bbdefb;
      padding: 20px;
      border: 1px solid #1976d2;
    }

    .sidebar {
      grid-column: 1 / 2; /* 从第1条网格线跨到第2条 */
      grid-row: 1 / 3;    /* 从第1条网格线跨到第3条 (占据两行) */
    }
    ```
    </details>

---

!!! example "display: none"

    `display: none` 会将元素从文档流中完全移除。它既不可见，也不占据任何空间，就好像它从未存在过一样。其子元素也会被一并移除。

    <div style="font-family: sans-serif; border: 2px dashed #ccc; padding: 10px;">
      <div style="background-color: #e0f7fa; border: 1px solid #00bcd4; padding: 10px;">这个元素是可见的。</div>
      <div style="display: none; background-color: #ffcdd2; border: 1px solid #f44336; padding: 10px;">这个元素被设置为 display: none，所以你看不见我。</div>
      <div style="background-color: #c8e6c9; border: 1px solid #4caf50; padding: 10px;">这个元素也是可见的，它紧跟着第一个元素。</div>
    </div>

    <details>
    <summary>点击查看源码</summary>

    ```html
    <div>
      <div class="box">这个元素是可见的。</div>
      <div class="box hidden">这个元素被设置为 display: none，所以你看不见我。</div>
      <div class="box">这个元素也是可见的，它紧跟着第一个元素。</div>
    </div>
    ```

    ```css
    .box {
      padding: 10px;
      border-width: 1px;
      border-style: solid;
    }
    .box:nth-of-type(1) { background-color: #e0f7fa; border-color: #00bcd4; }
    .box:nth-of-type(3) { background-color: #c8e6c9; border-color: #4caf50; }
    .hidden {
      display: none;
      background-color: #ffcdd2;
      border-color: #f44336;
    }
    ```
    </details>

## 实践技巧与注意事项 (Practical Tips & Notes)

!!! warning "注意事项"

    *   **`inline-block` 与空白符**：使用 `display: inline-block` 的元素会像文字一样受 HTML 中的空白符（空格、换行）影响，导致元素间出现不必要的间隙。解决方法包括移除 HTML 中的空白、将父元素 `font-size` 设为 0，或使用负 `margin`。
    *   **`display: none` vs `visibility: hidden`**：`display: none` 将元素从文档流中彻底移除，不占空间。而 `visibility: hidden` 仅在视觉上隐藏元素，但它仍然占据原来的空间。
    *   **Flex/Grid 容器与子项**：`display: flex` 或 `display: grid` 只直接影响其子元素。孙代元素不会自动成为 flex/grid 项。
    *   **`display: contents` 的作用**：这个值很特殊，它会使元素自身在布局树中消失，但其子元素会“继承”其位置，仿佛直接属于父级的父级。这在需要改变 DOM 结构以适应 Flexbox 或 Grid 布局但又不想添加额外包裹层时很有用。但请注意，应用了 `display: contents` 的元素本身的可访问性（ARIA roles, etc.）可能会丢失。
    *   **`display` 和 `float` 的冲突**：如果一个元素同时设置了 `display: inline` 和 `float` (非 `none`)，它的 `display` 值会计算为 `block`。同样，`display: inline-block` 也会表现得像 `block`。Flex 项和 Grid 项设置的 `float` 属性也会失效。

!!! tip "实践技巧"

    *   **现代布局首选**：对于任何非简单的布局需求，优先使用 `Flexbox`（一维布局）和 `Grid`（二维布局），而不是依赖 `inline-block` 或 `float`。它们更强大、更可预测。
    *   **创建块格式化上下文 (BFC)**：`display: flow-root` 是专门用来创建一个新的 BFC 的标准方法，可以用来清除浮动或防止外边距折叠，而不会带来其他副作用。`display: flex`, `grid`, `inline-block` 等也会创建 BFC。
    *   **重置样式**：在一个 CSS 重置表中，通常会为 HTML5 的新语义元素（如 `article`, `aside`, `nav`, `section`）设置 `display: block`，以确保它们在旧浏览器中被正确渲染为块级元素。
    *   **响应式设计**：`display` 是响应式设计的核心属性之一。通过媒体查询（`@media`），你可以根据屏幕尺寸改变元素的 `display` 值，例如，将桌面端的 `display: flex` 在移动端变为 `display: block`。

## 关联项 (Related Items)

-   **`position`**: 该属性与 `display` 共同决定元素的布局。例如，`position: absolute` 会使元素的 `display` 计算值为 `block` 类型。
-   **`float`**: 在 Flexbox 和 Grid 出现之前，`float` 是主要的布局工具之一。它与 `display` 的交互规则比较复杂（见上方注意事项）。
-   **`visibility`**: `visibility: hidden` 是另一种隐藏元素的方式，但它与 `display: none` 的核心区别在于是否保留元素所占的空间。
-   **`flex` / `grid` 相关属性**: 当设置 `display: flex` 或 `display: grid` 时，一系列新属性（如 `justify-content`, `align-items`, `grid-template-columns` 等）会生效，用于控制其子项的布局。
-   **`box-sizing`**: 理解 `display: block` 元素的尺寸模型时，`box-sizing` 属性至关重要，它决定了 `width` 和 `height` 是否包含 `padding` 和 `border`。
