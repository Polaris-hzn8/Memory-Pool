# 内存池

---

- SGI STL二级空间配置器内存池设计
- nginx内存池设计

不论是C语言的malloc\free还是C++中的new\delete（实际调用的也是malloc\free）操作，

如果在应用场景中涉及小块内存的开辟与释放（短时间内的内存进行频繁的开辟与释放），如果也频繁使用malloc/free操作，对应用程序的运行，在内存管理这一块的效率将会很低（降低了整个系统的性能），

这时便可以采用内存池的设计，对于小块内存频繁的开辟和释放，进行内存池的管理，从而优化提高系统的性能。

### SGI STL

SGI STL中的内存池设计，

```cpp
template<typename T, typename _Alloc=allocator<T>>
class vector{ };
```

#### 1.C++STL

关于C++中标准库STL中的allocator空间适配器，

allocator分离了对象的内存开辟、对象构造，分离了对象的内存释放、对象析构，

- allocate：负责给容器开辟内存空间，malloc
- deallocate：负责释放容器内存空间，free
- construct：负责给容器构造一个对象，通过定位new实现
- destroy：负责析构容器的对象，调用对象的析构函数

#### 2.SGI STL

关于SGI STL中的allocator空间适配器，提供了两个allocator的实现，分为两个allocator实现

- 一级allocator：内存管理使用malloc/free，
- 二级allocator：内存管理使用内存池进行优化，





### nginx

nginx中的内存池设计，

```cpp

```





















