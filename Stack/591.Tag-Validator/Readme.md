### 591.Tag-Validator

此题的表述非常复杂，需要逐条分析，各个击破。

1. 首先检测 cdata 的段首标记，有的话就开启 cdata_flag。在遇到cdata段尾标志前，所有字符不用check。
2. 其次检测 cdata 的段尾标记，有的话就关闭 cdata_flag。
3. 接着检测 tag 的段首标记，有的话就记录下这段TagName。需要顺次做这些工作：检测TagName是否合法；将TagName推入堆栈；如果是第一次进栈，则必须要保证这个Tag是整个code字符串的开头。
4. 最后检测 tag 的段尾标记，有的话就记录下这段TagName。需要顺次做这些工作：检测agName是否和栈顶的tag匹配；如果是最后一次进栈（即栈顶元素只有一个），则必须要保证这个Tag是整个code字符串的末尾。
5. 在遍历完整个code字符串之后，还要保证栈空，且栈曾经非空过。
