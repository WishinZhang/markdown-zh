<h2 id="overview">概述</h2>

<h3 id="philosophy">设计理念</h3>

Markdown 致力于使阅读和创作文档变得容易.

Markdown 视可读性为最高准则. Markdown 文件应该以纯文本形式原样发布, 不应该包含标记标签和格式化指令. 尽管
Markdown 的语法受到了以下这些 text-to-HTML
过滤器的影响 -- 包括 [Setext] [1], [atx] [2], [Textile] [3], [reStructuredText] [4],
[Grutatext] [5], 还有 [EtText] [6] --  但是 Markdown 语法灵感最大的来源还是纯文本 email 的格式.

  [1]: http://docutils.sourceforge.net/mirror/setext.html
  [2]: http://www.aaronsw.com/2002/atx/
  [3]: http://textism.com/tools/textile/
  [4]: http://docutils.sourceforge.net/rst.html
  [5]: http://www.triptico.com/software/grutatxt.html
  [6]: http://ettext.taint.org/doc/

基于以上背景, Markdown 完全由标点符号组成, 这些标点经过仔细挑选以使他们看上去和表达的含义相同. 例如, 星号标记的单词就像
 \*强调\*. 列表就像是列表. 如果你使用过 email 的话, 就连块引用都像引用的文本段落.



<h3 id="html">内联 HTML</h3>

Markdown 是用于 *创作* web 文档的.

Markdown 从来都不是要取代 HTML . 它的语法集非常小, 只对应一小部分
HTML 标签. 它要做的 *不是* 创造一种新的语法以使插入 HTML 标签变得更容易. 在我看来, HTML 标签已经很容易插入了. Markdown 的目标是易于阅读, 创作和编辑文章. HTML 是一种 *发布* 格式; Markdown 是一种 *创作*
格式. 因此, Markdown 处理的都是纯文本.

对于 Markdown 中未包含的标签, 可以直接使用 HTML. 没有必要使用定界符或标识符来表明从 Markdown 切换到 HTML; 直接使用标签就行了.

唯一的限制就是对于 HTML 块级元素 -- 像 `<div>`,
`<table>`, `<pre>`, `<p>`, 等等. -- 必须另起一行单独放 , 并且开始和结束标签前面不能有任何缩进. Markdown 会自动识别这些块级元素而不会在他们周围添加额外的 `<p>` 标签.

例如, 下面是添加 HTML 表格到 Markdown 文件:

    This is a regular paragraph.

    <table>
        <tr>
            <td>Foo</td>
        </tr>
    </table>

    This is another regular paragraph.

注意 Markdown 语法结构在 HTML 块级元素中不会被处理. 例如, 你不该在 HTML 块级元素中使用 Markdown 式的语法如 `*emphasis*` .

HTML 内联元素 -- 例如 `<span>`, `<cite>`, 和 `<del>` -- 可以在 Markdown 段落, 列表项, 标题中任意使用. 如果你乐意, 你甚至可以使用 HTML 标签替代 Markdown 格式; 例如你可以用 HTML `<a>` 和 `<img>` 标签替代 Markdown 的链接和图片语法.

不同于 HTML 块级元素, Markdown 语法*可以* 在内联元素中解析.


<h3 id="autoescape">特殊字符自动转义</h3>

在 HTML 中, 有两个字符需要特殊对待: `<`
和 `&`. 左尖括号用于起始标签; 英镑符号用于表示 HTML 字符实体. 如果你想将它们用作字面量, 你必须将它们转义为字符实体, 例如 `&lt;`, 和
`&amp;`.

英镑符号尤其使网页作者备受折磨. 如果你想得到 'AT&T', 你得这样写 '`AT&amp;T`'. 你甚至需要转义 URL 中的英镑符号. 因此, 如果你想链接到:

    http://images.google.com/images?num=30&q=larry+bird

你需要编码 `href` 属性为:

    http://images.google.com/images?num=30&amp;q=larry+bird

不用说, 这很容易被忘记, 也是 HTML 校验中最容易出现的错误.

你可以在 Markdown 中自由地使用这些字符, 这些字符在生成 HTML 时会被自动转义. 如果你在 HTML 字符实体中使用英镑符号, 它将保持不变; 否则它将被转义为 `&amp;`.

因此, 如果你需要得到版权符号, 可以写:

    &copy;

Markdown 不会将其转义. 但是如果你写:

    AT&T

Markdown 会将其转义:

    AT&amp;T

类似的, 由于 Markdown 支持 [内联 HTML](#html), 如果你使用尖括号作为 HTML 标签定界符, Markdown 将不会进行转义. 但是如果你写:

    4 < 5

Markdown 会将其转义:

    4 &lt; 5

总而言之, Markdown 的块级元素和内联元素中, 尖括号和英镑符号 *总是* 被自动编码. 这使得用
Markdown 来写 HTML 代码很容易. (相较之下, 原始的 HTML 中就很难书写 HTML 代码, 因为代码中的每个 `<`
和 `&` 都需要被转义.)
