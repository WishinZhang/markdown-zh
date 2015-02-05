<h2 id="span">内联元素</h2>

<h3 id="link">链接</h3>

Markdown 支持两种链接形式: *内联* 和 *引用*.

这两种形式下链接文本的定界符都是 [中括号].

要创建内联链接, 只需在链接文本的右括号后面紧接一对圆括号. 圆括号里面放所需的 URL 链接, 还可以放一个 *可选* 的链接标题, 标题要用引号包围. 例如:

    This is [an example](http://example.com/ "Title") inline link.

    [This link](http://example.net/) has no title attribute.

将会生成:

    <p>This is <a href="http://example.com/" title="Title">
    an example</a> inline link.</p>

    <p><a href="http://example.net/">This link</a> has no
    title attribute.</p>

如果是引用相同服务器下的本地资源, 还可以用相对路径:

    See my [About](/about/) page for details.

引用类型的链接放在第二个中括号里, 括号里面放链接标签:

    This is [an example][id] reference-style link.

两个中括号之间可以有空格:

    This is [an example] [id] reference-style link.

接下来, 在文档中的任意位置, 你可以像下面那样定义链接标签,
需要单独占一行:

    [id]: http://example.com/  "Optional Title Here"

也就是:

*   方括号中包含链接标识符 (可以用三个以上的空白符来添加缩进);
*   跟着是冒号;
*   跟着是一个以上的空白符和水平制表符;
*   跟着是链接的 URL;
*   跟着是可选的标题属性, 可以用单引号, 双引号, 或者圆括号包围.

以下三个链接的定义是等价的:

	[foo]: http://example.com/  "Optional Title Here"
	[foo]: http://example.com/  'Optional Title Here'
	[foo]: http://example.com/  (Optional Title Here)

**注意:** Markdown.pl 1.0.1 有一个已知的问题就是不能用单引号来包围链接标题.

URL 可以用尖括号包围:

    [id]: <http://example.com/>  "Optional Title Here"

对于较长的 URL , 为了美观起见, 你可以另起一行放置链接标题, 需要在前面加额外的水平制表符或空格作为内间距:

    [id]: http://example.com/longish/path/to/resource/here
        "Optional Title Here"

链接定义只存在于 Markdown 处理期间, 而不会在最终的 HTML 出现.

链接定义的名称可以包含字母, 数字, 空格, 和标点符号 -- 但它们 *不是* 大小写敏感的. 例如, 下面两个链接是等价的:

	[link text][a]
	[link text][A]

*隐含链接名称* 使你可以忽略链接名称, 这时链接文本本身被用于链接名称.
只用一对空的中括号就可以了 -- 例如, 要链接
"Google" 这个词到 google.com 网站, 你只用这样写:

	[Google][]

同时这样定义链接:

	[Google]: http://google.com/

由于链接名称可以包含空格, 甚至链接文本中包含多个单词时这种快捷方式也是可行的:

	Visit [Daring Fireball][] for more information.

链接定义如下:

	[Daring Fireball]: http://daringfireball.net/

链接定义可以放在 Markdown 文档的任意位置. 一般倾向于将它们直接放在引用位置下面, 当然, 也可以像底部注释那样, 将它们都放在文档底部.

下面是一个引用链接实例:

    I get 10 times more traffic from [Google] [1] than from
    [Yahoo] [2] or [MSN] [3].

      [1]: http://google.com/        "Google"
      [2]: http://search.yahoo.com/  "Yahoo Search"
      [3]: http://search.msn.com/    "MSN Search"

要使用默认链接, 可以这样写:

    I get 10 times more traffic from [Google][] than from
    [Yahoo][] or [MSN][].

      [google]: http://google.com/        "Google"
      [yahoo]:  http://search.yahoo.com/  "Yahoo Search"
      [msn]:    http://search.msn.com/    "MSN Search"

上面两个例子都会输出以下 HTML:

    <p>I get 10 times more traffic from <a href="http://google.com/"
    title="Google">Google</a> than from
    <a href="http://search.yahoo.com/" title="Yahoo Search">Yahoo</a>
    or <a href="http://search.msn.com/" title="MSN Search">MSN</a>.</p>

作为对比, 下面是用 Markdown 内联链接的效果:

    I get 10 times more traffic from [Google](http://google.com/ "Google")
    than from [Yahoo](http://search.yahoo.com/ "Yahoo Search") or
    [MSN](http://search.msn.com/ "MSN Search").

引用连接的意义不在于更容易书写, 而在于使得文档更易于阅读. 比较上面两个例子: 使用引用链接的段落只有 81 个字符; 使用内联链接的段落有 176 个字符; 而原始的 HTML 有 234 个字符. 在原始的 HTML 中, 标记比文本还多.

使用 Markdown 的引用链接, 源码更接近与最终的输出, 就像浏览器中呈现的样子. 通过把标记元数据移出段落,
你可以不用打断行文而直接添加链接.


<h3 id="em">强调</h3>

Markdown 将星号 (`*`) 和下划线 (`_`) 作为强调标记. 用 `*` 或者 `_` 包裹的文本将会用
HTML `<em>` 标签包裹; 双 `*` 或者 `_` 将会用 HTML
`<strong>` 标签包裹. 例如, 下面的输入:

    *single asterisks*

    _single underscores_

    **double asterisks**

    __double underscores__

会输出:

    <em>single asterisks</em>

    <em>single underscores</em>

    <strong>double asterisks</strong>

    <strong>double underscores</strong>

两种形式可以任意选择, 但是同一片段的开关标记必须一致.

强调可以用在单词中:

    un*frigging*believable

但是如果 `*` 或者 `_` 两边都有空格, 则会被视为星号和下划线的字面量.

要使用星号和下划线字面量, 需要进行转义, 以区别于强调:

    \*this text is surrounded by literal asterisks\*



<h3 id="code">代码</h3>

要输出一个代码片段, 需要使用重音符号 (`` ` ``).
不同于预格式的代码块, 代码片段只是在普通段落中标识出代码. 例如:

    Use the `printf()` function.

会生成:

    <p>Use the <code>printf()</code> function.</p>

要在代码片段中包含字面量的重音符号, 可以使用多个重音符号作为起始和结束标记:

    ``There is a literal backtick (`) here.``

会生成:

    <p><code>There is a literal backtick (`) here.</code></p>

包含代码片段的重音符号可以包含空格 --
起始标记后一个, 结束标记前一个. 这使你可以在代码片段开始和结束位置使用重音符号的字面量:

	A single backtick in a code span: `` ` ``

	A backtick-delimited string in a code span: `` `foo` ``

会生成:

	<p>A single backtick in a code span: <code>`</code></p>

	<p>A backtick-delimited string in a code span: <code>`foo`</code></p>

在代码片段中, 英镑符号和尖括号会被转换成相应的字符实体, 这使得包含 HTML
标签很容易. Markdown 会将下面的代码:

    Please don't use any `<blink>` tags.

转成:

    <p>Please don't use any <code>&lt;blink&gt;</code> tags.</p>

这样写:

    `&#8212;` is the decimal-encoded equivalent of `&mdash;`.

会生成:

    <p><code>&amp;#8212;</code> is the decimal-encoded
    equivalent of <code>&amp;mdash;</code>.</p>



<h3 id="img">图片</h3>

通常, 要用 "原生" 的语法在纯文本格式中插入图片是很困难的.

Markdown 使用了类似链接的语法来插入图片, 包含两种形式: *内联* 和 *引用*.

内联图片语法如下:

    ![Alt text](/path/to/img.jpg)

    ![Alt text](/path/to/img.jpg "Optional title")

也就是:

*   一个感叹号: `!`;
*   紧跟着一对方括号, 包含了图片的 `alt`
    属性;
*   紧跟着一对圆括号, 包含了图片的 URL 或者路径, 以及一个可选的用单引号或双引号包裹的 `title` 属性.

引用图片语法如下:

    ![Alt text][id]

"id" 是图片引用的名称. 图片引用使用链接定义的相同语法:

    [id]: url/to/image  "Optional title attribute"

Markdown 没有语法指定图片尺寸; 如果需要指定图片尺寸, 可以使用 HTML `<img>` 标签.

