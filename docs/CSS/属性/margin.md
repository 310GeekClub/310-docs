# `margin`

## 简介 (Introduction)

`margin` 属性用于设置元素边框（border）外部的空白区域，即外边距，它控制着元素与相邻元素之间的距离。

## 语法 (Syntax)

`margin` 是一个简写属性，可以接受一到四个值。

```css
/* 可以使用的值类型 */
margin: <length>; /* 例如 10px, 1.5em */
margin: <percentage>; /* 例如 5% */
margin: auto; /* 特殊关键字，常用于居中 */

/* 值的数量决定了它们如何应用 */
/* 1 个值: 应用于所有四个方向 */
margin: 10px; /* 上下左右均为 10px */

/* 2 个值: 第一个用于上下，第二个用于左右 */
margin: 10px 20px; /* 上下 10px, 左右 20px */

/* 3 个值: 第一个用于上，第二个用于左右，第三个用于下 */
margin: 10px 20px 30px; /* 上 10px, 左右 20px, 下 30px */

/* 4 个值: 按上、右、下、左的顺序应用 (顺时针) */
margin: 10px 20px 30px 40px; /* 上 10px, 右 20px, 下 30px, 左 40px */

/* 全局值 */
margin: inherit;
margin: initial;
margin: revert;
margin: revert-layer;
margin: unset;
```

它也是以下四个属性的简写：

-   `margin-top`
-   `margin-right`
-   `margin-bottom`
-   `margin-left`

## 核心用法与示例 (Core Usage & Examples)

---

!!! example "设置元素间距"

    `margin` 最基础的用途是创建元素之间的视觉间隔。下面的示例使用 `margin-bottom` 在堆叠的块之间创建了垂直间距。

    <div style="font-family: sans-serif; border: 2px dashed #ccc; padding: 10px;">
      <div style="background-color: #e0f7fa; border: 1px solid #00bcd4; padding: 15px; margin-bottom: 20px;">我是第一个盒子。我的 `margin-bottom` 是 20px。</div>
      <div style="background-color: #e0f7fa; border: 1px solid #00bcd4; padding: 15px; margin-bottom: 20px;">我是第二个盒子。</div>
      <div style="background-color: #e0f7fa; border: 1px solid #00bcd4; padding: 15px;">我是第三个盒子。</div>
    </div>

    <details>
    <summary>点击查看源码</summary>

    ```html
    <div class="container">
      <div class="box">我是第一个盒子。我的 `margin-bottom` 是 20px。</div>
      <div class="box">我是第二个盒子。</div>
      <div class="box">我是第三个盒子。</div>
    </div>
    ```

    ```css
    .box {
      background-color: #e0f7fa;
      border: 1px solid #00bcd4;
      padding: 15px;
    }
    .box:not(:last-child) {
      margin-bottom: 20px;
    }
    ```
    </details>

---

!!! example "使用 auto 实现水平居中"

    将块级元素（`display: block`）的左右外边距设置为 `auto`，并为其指定一个明确的 `width`，是实现水平居中的经典方法。浏览器会自动计算并平均分配左右的剩余空间。

    <div style="font-family: sans-serif; border: 2px dashed #ccc; padding: 10px; background: #f3f3f3;">
      <div style="background-color: #ffcdd2; border: 1px solid #f44336; padding: 20px; width: 60%; margin: 20px auto;">
        我的 `width` 是 60%，`margin` 是 `20px auto`。
        <br>
        所以垂直外边距是 20px，并且我水平居中了。
      </div>
    </div>

    <details>
    <summary>点击查看源码</summary>

    ```html
    <div class="parent">
      <div class="centered-box">
        我的 `width` 是 60%，`margin` 是 `20px auto`。
        <br>
        所以垂直外边距是 20px，并且我水平居中了。
      </div>
    </div>
    ```

    ```css
    .parent {
      background: #f3f3f3;
      /* 父元素用于演示效果 */
    }
    .centered-box {
      background-color: #ffcdd2;
      border: 1px solid #f44336;
      padding: 20px;
      width: 60%;
      /*
        上下外边距 20px,
        左右外边距自动分配，实现居中
      */
      margin: 20px auto;
    }
    ```
    </details>

---

!!! example "使用负外边距创建重叠效果"

    外边距可以设置为负值。这会导致元素向该方向移动，甚至与其他元素发生重叠，常用于创建特殊的视觉效果。

    <div style="font-family: sans-serif; border: 2px dashed #ccc; padding: 10px 10px 30px 10px; background: #fafafa;">
      <div style="background-color: #c8e6c9; border: 1px solid #4caf50; padding: 20px; width: 80%; height: 80px;">盒子 1</div>
      <div style="background-color: #bbdefb; border: 1px solid #1976d2; padding: 20px; width: 80%; margin-top: -30px; margin-left: 30px; position: relative;">
        盒子 2 (margin-top: -30px)
      </div>
    </div>

    <details>
    <summary>点击查看源码</summary>

    ```html
    <div>
      <div class="box1">盒子 1</div>
      <div class="box2">盒子 2 (margin-top: -30px)</div>
    </div>
    ```

    ```css
    .box1 {
      background-color: #c8e6c9;
      border: 1px solid #4caf50;
      padding: 20px;
      width: 80%;
      height: 80px;
    }
    .box2 {
      background-color: #bbdefb;
      border: 1px solid #1976d2;
      padding: 20px;
      width: 80%;
      /* 向上移动 30px，与上一个元素重叠 */
      margin-top: -30px;
      /* 同时向右移动，以获得更好的视觉效果 */
      margin-left: 30px;
      /* 提升层叠上下文，确保文本可见 */
      position: relative;
    }
    ```
    </details>

## 实践技巧与注意事项 (Practical Tips & Notes)

!!! warning "外边距折叠 (Margin Collapsing)"

    这是 `margin` 最重要的特性之一。在某些情况下，相邻的垂直外边距会合并（折叠）成一个单一的外边距，其大小等于两个外边距中较大的那个值。

    *   **相邻兄弟元素**：两个在文档流中相邻的块级兄弟元素的 `margin-bottom` 和 `margin-top` 会发生折叠。
    *   **父元素与子元素**：如果父元素没有 `border`、`padding`、`inline content` 或 `clearance` 来分隔它和第一个/最后一个子元素的外边距，那么父元素的 `margin-top` 会和第一个子元素的 `margin-top` 折叠，`margin-bottom` 会和最后一个子元素的 `margin-bottom` 折叠。
    *   **空块元素**：如果一个块级元素为空（没有内容、内边距、边框或高度），它自身的 `margin-top` 和 `margin-bottom` 也会折叠。
    *   **如何防止**：创建新的块格式化上下文 (BFC) 可以防止外边距折叠。例如给父元素设置 `display: flow-root;`、`overflow: auto;` 或 `display: flex;`。

!!! warning "行内元素的垂直外边距"

    `margin-top` 和 `margin-bottom` 对非替换行内元素（如 `<span>`, `<a>`）没有视觉效果。它们不会将上方或下方的行推开。但是，水平方向的 `margin-left` 和 `margin-right` 是有效的。

!!! tip "百分比外边距的计算基准"

    当 `margin` 的值是百分比时，无论是垂直方向（`margin-top`/`bottom`）还是水平方向（`margin-left`/`right`），其计算的基准都是**其包含块（containing block）的宽度（width）**。这是一个常见的误解点。

!!! tip "简写与覆盖"

    使用 `margin` 简写属性会覆盖之前设置的所有单个 `margin-*` 属性。例如，在 `margin-top: 20px;`之后写 `margin: 10px;`，最终 `margin-top` 的值会是 `10px` 而不是 `20px`。

## 关联项 (Related Items)

-   **`padding`**: 定义元素边框内部的空白区域（内边距），它与 `margin` 共同构成了 CSS 盒模型的核心部分。
-   **`border`**: 位于 `margin` 和 `padding` 之间的边界线。
-   **`box-sizing`**: 决定了元素的 `width` 和 `height` 属性是包含 `padding` 和 `border`（`border-box`），还是不包含（`content-box`），这间接影响了布局和外边距的应用。
-   **`display`**: 元素的 `display` 类型（如 `block`, `inline`, `inline-block`）直接决定了其外边距的行为方式，例如行内元素垂直外边距无效，以及是否会发生外边距折叠。
-   **`overflow`**: 设置 `overflow` 为 `auto`, `hidden` 或 `scroll` (除了 `visible`) 可以为元素创建新的块格式化上下文（BFC），从而阻止其内部子元素的外边距与外部元素发生折叠。
