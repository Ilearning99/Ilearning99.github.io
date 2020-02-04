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

vector尾部增加删除元素：
```.c
#include<vector>
using namespace std;
vector<int> vint;
vint.push_back(1);
vint.pop_back();
```

string字符串初始化：
```.c
#include<string>
using namespace std;

string s(10,' '); // 10个' '构成的字符串
```

queue的基本操作
```.c
#include<queue>
using namespace std;

queue<int> que;
que.push(1); // 队尾加入数据
que.front(); // 队首元素
que.pop(); // 队首删除元素
que.back(); // 返回队尾元素
```

## 指针相关

定义多个指针，*跟在变量名前：

```.c
int *a,*b,*c;
```

## 常量

整数最大值、最小值：INT_MAX INT_MIN

空指针：nullptr（关键字）