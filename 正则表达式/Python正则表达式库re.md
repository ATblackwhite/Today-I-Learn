python使用re库来用正则表达式匹配字符串
```python
import re
pattern = re.compile(exp)
content = pattern.findall(string) # 选出字符串中符合正则表达式的部分
replaced_text = re.sub(pattern, word, text) # 替换字符串中符合正则表达式的部分
```

python正则表达式内容与大多数都相同
`(?:)`: 这是一个非捕获组，用于分组正则表达式的一部分，但不保存该部分的匹配结果。
`.*?`: 这是一个非贪婪匹配符，`.`匹配除换行符之外的任何单个字符，`*`表示匹配前面的元素零次或多次，`?`使匹配变成非贪婪模式，即尽可能少地匹配字符。
`\b \b`: 是一个单词边界符，确保只匹配单独的字母
`\s`: 匹配任何空白字符，包括空格、制表符、换行符等。
`\s+`: 匹配一个或多个空白字符