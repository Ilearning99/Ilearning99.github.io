# 单例模式
对应类型只初始化一个实例。

### 饿汉式
```.c
class singleton
{
    private static singleton _helper = new singleton();

    public static single GetInstance()
    {
        return _helper;
    }
}
```



### 懒汉式
```.c
class singleton
{
    private static singleton _helper = null;
    private static object locker = new object();

    public static singleton GetInstance()
    {
        if (_helper == null)
        {
            lock (locker)
            {
                if (_helper == null)
                {
                    _helper = new singleton();
                }
            }
        }
        return _helper;
    }
}
```