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

string字符串基本操作：
```.c
#include<string>
using namespace std;

string s(10,' '); // 初始化为10个' '构成的字符串
printf("%s",s.c_str()); // 返回const char*型指针
s.substr(id,len); // 返回从id开始，len长度的字符串
return s==s1; // 比较两个字符串是否相等
```

queue的基本操作
```.c
#include<queue>
using namespace std;

queue<int> que;
que.push(1); // 队尾加入数据
int h=que.front(); // 队首元素
que.pop(); // 队首删除元素
que.back(); // 返回队尾元素
```

set的基本操作
```.c
#include<set>
#include<vector>
using namespace std;

vector<int> v(5,0);
set<int> mset(v.begin(),v.end()); //set初始化
mset.insert(3); //插入set
set<int>::iterator iter=mset.find(2); //查找元素
```

deque双端队列基本操作
```.c
#include<deque>
using namespace std;

deque<int> d;
d.push_back(10); // 队尾插入元素
d.push_front(3); // 队首插入元素
cout<<d.front()<<endl; // 队首元素
cout<<d.back()<<endl; // 队尾元素
d.pop_back(); // 从队尾弹出元素
d.pop_front(); // 从队首弹出元素
```

priority_queue优先队列基本操作
```.c
#include<queue>
using namespace std;

priority_queue<int> pq; // 默认最大堆
pq.push(1); // 优先队列加入数据
int h=pq.top(); // 返回堆顶元素
pq.pop(); // 弹出堆顶元素

struct cmp{
    bool operator()(int&a, int&b){
        return a>b;
    }
};
priority_queue<int,vector<int>,cmp> pqmin; //自定义比较函数(小顶堆)
```

map的遍历
```.c
#include<map>
using namespace std;

map<int,int> mint;
map<int,int>::iterator iter;
for(iter=mint.begin();iter!=mint.end();iter++){
    printf("%d %d\n",iter->first,iter->second);
}
mint.erase(key); // 删除对应键值对
```

二分查找
```.c
#include<algorithm>
#include<vector>
using namespace std;

int target;
vector<int> v;
vector<int>::iterator low,up;
low=lower_bound(v.begin(),v.end(),target); //第一个大于等于target的值
up=upper_bound(v.begin(),v.end(),target); //第一个大于target的值
```

reverse反转数组
```.c
#include<algorithm>
using namespace std;

vector<int> v;
reverse(v.begin(),v.end());
```

字符串与数字相互转换
```.c
#include<sstream>
#include<string>
using namespace std;

// 数字转字符串
double num=123.32;
string str;
stringstream ss;
ss<<num;
ss>>str;
// 字符串转数字
ss<<str;
ss>>num;
// 字符串转整型数字
string tmp="123";
int tmpnum=atoi(tmp.c_str());
```

内置函数
```.c
__builtin_popcount(n); // 统计n中有多少个1
```

## 指针相关

定义多个指针，*跟在变量名前：

```.c
int *a,*b,*c;
```

## 常量

整数最大值、最小值：INT_MAX INT_MIN

空指针：nullptr（关键字）