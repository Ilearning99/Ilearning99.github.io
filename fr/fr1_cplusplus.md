# C++备忘

## stl库相关

对vector进行排序: 

```.c
#include<algorithm>
sort(vector.begin(),vector.end());
```

是否是数字(0-9)：
```.c
#include<cctype>
isdigit(str[i]);
```

是否是字母(a-zA-Z)：
```.c
#include<cctype>
isalpha(str[i]);
```

转为小写字母：
```.c
#include<cctype>
str[i]=tolower(str[i]);
```

## 指针相关

定义多个指针，*跟在变量名前：

```.c
int *a,*b,*c;
```