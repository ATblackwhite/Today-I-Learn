在C#中，字符串类型和JAVA中类似，都是类的一种。
但是C#中可以使用System.String的别名——“string”来声明String类

String类的常用属性有
>Length    表示字符串的长度

常用属性有
>Equals() 注意判断两个字符串是否相同要用这个方法，虽然C#有符号重载但仍然使用这个方法

字符串是值为文本的 [String](https://learn.microsoft.com/zh-cn/dotnet/api/system.string) 类型对象。 文本在内部存储为 [Char](https://learn.microsoft.com/zh-cn/dotnet/api/system.char) 对象的依序只读集合。
因此，string中的字符是无法更改的，也就是说你无法做到以下操作
```C#
string s = "abcd";
s[0] = 'b'; //使用此操作会报错
```
然而，我们可以使用 [StringBuilder](https://learn.microsoft.com/zh-cn/dotnet/api/system.text.stringbuilder) 对象“就地”修改各个字符，再新建字符串来使用 [StringBuilder](https://learn.microsoft.com/zh-cn/dotnet/api/system.text.stringbuilder) 方法存储结果。
```C#
string question = "hOW DOES mICROSOFT wORD DEAL WITH THE cAPS lOCK KEY?";
System.Text.StringBuilder sb = new System.Text.StringBuilder(question);

for (int j = 0; j < sb.Length; j++)
{
    if (System.Char.IsLower(sb[j]) == true)
        sb[j] = System.Char.ToUpper(sb[j]);
    else if (System.Char.IsUpper(sb[j]) == true)
        sb[j] = System.Char.ToLower(sb[j]);
}
// Store the new string.
string corrected = sb.ToString();
System.Console.WriteLine(corrected);
// Output: How does Microsoft Word deal with the Caps Lock key?