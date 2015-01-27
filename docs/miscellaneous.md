<h2 id="misc">其他</h2>

<h3 id="autolink">自动链接</h3>

Markdown 支持一种 "自动" 创建 URL 和 email 地址链接的简短形式: 只需用尖括号包围 URL 或 email 地址即可. 这意味着如果你想为 URL 和 email 链接加上可点击的链接, 你只需要这样写:

    <http://example.com/>

Markdown 将把它转化为:

    <a href="http://example.com/">http://example.com/</a>

email 链接也是一样, 除此之外, Markdown 还会随机添加十进制和十六进制字符实体引用来帮助你混淆邮件地址以屏蔽广告和垃圾邮件爬虫. 例如, Markdown 会将如下代码:

    <address@example.com>

转化为:

    <a href="&#x6D;&#x61;i&#x6C;&#x74;&#x6F;:&#x61;&#x64;&#x64;&#x72;&#x65;
    &#115;&#115;&#64;&#101;&#120;&#x61;&#109;&#x70;&#x6C;e&#x2E;&#99;&#111;
    &#109;">&#x61;&#x64;&#x64;&#x72;&#x65;&#115;&#115;&#64;&#101;&#120;&#x61;
    &#109;&#x70;&#x6C;e&#x2E;&#99;&#111;&#109;</a>

这在浏览器中会渲染为可点击的 "address@example.com" 链接.

(这种字符实体编码的小把戏确实可以欺骗一些简单的广告和垃圾邮件爬虫, 但是不足以欺骗所有爬虫. 虽然聊胜于无, 但是这种形式发布的邮件地址最终还是会收到垃圾邮件的.)



<h3 id="backslash">反斜杠转义</h3>

Markdown 中可以使用反斜杠转义 Markdown 语法符号为字面量. 例如, 如果你想用星号包围一个单词 (而不是 HTML 的 `<em>` 标签), 你可以在星号前面加反斜杠, 就像这样:

    \*literal asterisks\*

Markdown 为下面字符提供反斜杠转义:

    \   backslash
    `   backtick
    *   asterisk
    _   underscore
    {}  curly braces
    []  square brackets
    ()  parentheses
    #   hash mark
	+	plus sign
	-	minus sign (hyphen)
    .   dot
    !   exclamation mark
