# C#相关知识

### 查找相关包版本

[nuget.org](https://www.nuget.org/) 可以查找函数需要的C#包以及相应的最新版本

### 正则匹配

- 匹配中文 [\u4e00-\u9fa5]
- 使用命名空间
```.c
using System.Text.RegularExpressions;
```

### 字符串操作

- 去掉字符串首尾不需要的字符，使用String自带的Trim函数
```.c
String message = " abc  ";
String cleanedMessage = message.Trim(new char[]{' ','/','\\','\''});
```

- json字符串解析，使用MongoDB


