<h2 id="block">块级元素</h2>


<h3 id="p">段落和换行</h3>

段落就是连续行上的文本, 一个或多个空行划分不同的段落. (空行的含义就只要是看起来是空行就行了 -- 即使包含了 spaces 或者 等空白符也是空行.) 普通段落不应该使用缩进.

段落是由一行或多行连续文本组成的, 这条规则使得 Markdown 支持 "硬换行". 这个其他的文本到HTML转换器有很大不同 (包括 Movable
Type 的 "Convert Line Breaks" 选项) , 通常这些转换器会将段落中的每个换行都转换为一个 `<br />` 标签.

当你 *确实需要* 在 Markdown 中输入 `<br />` 标签, 只需要在行尾加上两个及以上的空格, 然后换行.

确实, 这样输入 `<br />` 麻烦了一点, 但是
"换行即 `<br />`" 的规则并不适用于 Markdown.
这时, 用硬换行来格式化 Markdown 中 email 式的 [blockquoting][bq] 以及多段落 [list items][l]
或许是更好的选择.

  [bq]: #blockquote
  [l]:  #list



<h3 id="header">标题</h3>

Markdown 支持两种形式的标题, [Setext] [1] 和 [atx] [2].

Setext 样式的标题使用的等号来表示一级标题, 使用连字符表示二级标题. 例如:

    This is an H1
    =============

    This is an H2
    -------------

任意长度的 `=` 或 `-` 都是可以的.

Atx 样式的标题每行开头使用 1-6 井号,
对应 1-6 级标题. 例如:

    # This is an H1

    ## This is an H2

    ###### This is an H6

可选地, 你可以 "关闭" atx 样式的标题. 这纯粹是美化需要 -- 如果你认为这样美观一些就用吧. 关闭标签的井号数量甚至不需要和起始位置的匹配. (起始的井号数量决定了标题的级别.) :

    # This is an H1 #

    ## This is an H2 ##

    ### This is an H3 ######


<h3 id="blockquote">块引用</h3>

Markdown 使用 email 样式的 `>` 字符作为块引用. 如果你熟悉 email 消息中的引用段落, 那么你同样可以在 Markdown 中创建块引用. 最好对引用文本采取强制换行并在每一行行首放一个 `>` :

    > This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
    > consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
    > Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.
    >
    > Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
    > id sem consectetuer libero luctus adipiscing.

Markdown 中可以简便地只在每一个需要强制换行的段落的首行前面加上一个 `>` :

    > This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
    consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
    Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.

    > Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
    id sem consectetuer libero luctus adipiscing.

块引用可以嵌套 (例如, 块引用中包含块引用) , 只需添加额外层级的 `>` 即可:

    > This is the first level of quoting.
    >
    > > This is nested blockquote.
    >
    > Back to the first level.

块引用可以包含 Markdown 元素, 包括标题, 列表和代码块:

	> ## This is a header.
	>
	> 1.   This is the first list item.
	> 2.   This is the second list item.
	>
	> Here's some example code:
	>
	>     return shell_exec("echo $input | $markdown_script");

任何合适的文本编辑器都应该可以很方便的创建 email 样式的块引用. 例如, 用 BBEdit 就可以选取文本然后从 'Text' 菜单中选择 'Increase
Quote Level'.


<h3 id="list">列表</h3>

Markdown 支持有序列表和无序列表.

无序列表使用星号, 加号, 和连字符 -- 这些符号是可互换的
-- 最为列表标记:

    *   Red
    *   Green
    *   Blue

等价于:

    +   Red
    +   Green
    +   Blue

以及:

    -   Red
    -   Green
    -   Blue

有序列表使用数字加句号:

    1.  Bird
    2.  McHale
    3.  Parish

需要注意的是这里的数字序号对于最终生成 HTML 是没有影响的.
这里 Markdown 输出的 HTML 列表是:

    <ol>
    <li>Bird</li>
    <li>McHale</li>
    <li>Parish</li>
    </ol>

即使你把列表写成这样:

    1.  Bird
    1.  McHale
    1.  Parish

甚至这样:

    3. Bird
    1. McHale
    8. Parish

你都讲得到相同的 HTML 输出. 重点是, 如果你希望你的 Markdown 源码中的列表序号匹配输出的 HTML 列表序号, 你应该使用正常的序号 .
当然, 如果你想简单点, 也可不必这么做.

即使你使用错误的列表序号, 最终生成的列表仍然会以序号 1 开始. 在未来的版本里, Markdown 可能支持以任意数字作为列表起始序号.

List 标记通常从左边开始, 可以用三个及以上的空格来缩进. List 标记后面应该跟一个以上的空格或者一个水平制表符.

为了使列表更美观, 可以用悬挂缩进来格式化列表项:

    *   Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
        Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi,
        viverra nec, fringilla in, laoreet vitae, risus.
    *   Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
        Suspendisse id sem consectetuer libero luctus adipiscing.

但是这不是必须的:

    *   Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
    Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi,
    viverra nec, fringilla in, laoreet vitae, risus.
    *   Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
    Suspendisse id sem consectetuer libero luctus adipiscing.

如果列表项中包含空行, Markdown 会在 HTML 输出中用 `<p>` 来包裹他们. 例如, 下面的输入:

    *   Bird
    *   Magic

会输出:

    <ul>
    <li>Bird</li>
    <li>Magic</li>
    </ul>

但是:

    *   Bird

    *   Magic

会输出:

    <ul>
    <li><p>Bird</p></li>
    <li><p>Magic</p></li>
    </ul>

列表项可能包含多个段落. 列表项中的每个段落都必须用 4 个空格或一个水平制表符来缩进:

    1.  This is a list item with two paragraphs. Lorem ipsum dolor
        sit amet, consectetuer adipiscing elit. Aliquam hendrerit
        mi posuere lectus.

        Vestibulum enim wisi, viverra nec, fringilla in, laoreet
        vitae, risus. Donec sit amet nisl. Aliquam semper ipsum
        sit amet velit.

    2.  Suspendisse id sem consectetuer libero luctus adipiscing.

同上, 悬挂缩进只是为了更美观, 而非强制要求:

    *   This is a list item with two paragraphs.

        This is the second paragraph in the list item. You're
    only required to indent the first line. Lorem ipsum dolor
    sit amet, consectetuer adipiscing elit.

    *   Another item in the same list.

如果列表项中包含块注释 , 块注释标记 `>`
需要缩进:

    *   A list item with a blockquote:

        > This is a blockquote
        > inside a list item.

如果列表项中有代码块, 代码块需要 *双倍* 缩进-- 8 个空格或者两个水平制表符:

    *   A list item with a code block:

            <code goes here>


有时候无意中出发有序列表, 如下面这样的代码:

    1986. What a great season.

即使, 如果一行开头满足 *number-period-space* 模式. 可以通过转义点号来避免这种情况:

    1986\. What a great season.



<h3 id="precode">代码块</h3>

预格式化的代码块用于输出编程语言和标记语言. 不同于普通段落, 代码块中的行会被原样呈现. Markdown 会用 `<pre>` 和 `<code>` 标签包围代码块.

要在 Markdown 中插入代码块, 只需要将每一行都缩进 4 个空格或者 1 个水平制表符. 例如, 下面的输入:

    This is a normal paragraph:

        This is a code block.

Markdown 会生成:

    <p>This is a normal paragraph:</p>

    <pre><code>This is a code block.
    </code></pre>

只有一级缩进 --  4 个空格或者 1 个水平制表符 -- 会从代码块中的每一行中移除. 例如:

    Here is an example of AppleScript:

        tell application "Foo"
            beep
        end tell

会生成:

    <p>Here is an example of AppleScript:</p>

    <pre><code>tell application "Foo"
        beep
    end tell
    </code></pre>

代码块自动扩展直到碰到未使用缩进的文本
(或者文章结尾).

在代码块内, 英镑符号 (`&`) 和尖括号 (`<` 和 `>`)
或自动转换为 HTML 字符实体. 这使得用 Markdown 包含 HTML 代码非常容易  -- 只需粘贴并缩进, Markdown 会自动转换字符实体. 例如:

        <div class="footer">
            &copy; 2004 Foo Corporation
        </div>

会生成:

    <pre><code>&lt;div class="footer"&gt;
        &amp;copy; 2004 Foo Corporation
    &lt;/div&gt;
    </code></pre>

Markdown 的语法在代码块中是无效的的. 例如,
代码块中的星号只是它的字面量而已. 这使得用 Markdown 来书写 Markdown 自身的语法很容易.



<h3 id="hr">水平线</h3>

如果一行中只有三个以上的连字符, 星号, 或者下划线则会在该位置生成一个 `<hr />` 标签. 星号和连字符之间的空格也是允许的. 下面的例子都会生成一条水平线:

    * * *

    ***

    *****

    - - -

    ---------------------------------------

