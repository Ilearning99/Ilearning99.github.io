# C# web应用

## 作用域和对象的释放行为

### 作用域
作用域必需实现IServiceScope

### 释放行为
类实现IDisposable接口，容器能自动释放实现该接口的类的对象，应当避免手动创建对象，使用容器自动创建并管理对象的生命周期。